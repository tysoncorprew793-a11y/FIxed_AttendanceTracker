# Importing the repaired Smart Attendance Tracker into Bolt

## Important
Bolt may not support uploading a ZIP directly as an existing app. The reliable route is to extract this ZIP, create a GitHub repository containing the contents of the `project` folder (not the parent folder), and use Bolt’s **Import from GitHub** option if available in your workspace. Alternatively, open the project in StackBlitz or a local VS Code environment.

## Before testing
1. In Bolt, use the existing database if possible. If you create a new database, apply the SQL migrations in timestamp order; these are schema definitions, not live data exports.
2. Confirm that `checkin_attempts` has `student_id` and an index on `(session_code, student_id, created_at)`. The migration `20261119220000_repair_checkin_attempts_student_id.sql` adds these if needed.
3. **Deploy the updated `supabase/functions/checkin/index.ts` function** to the database project used by the app. Importing frontend source alone does not necessarily deploy Edge Functions.
4. Set `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` for the frontend, and keep `SUPABASE_SERVICE_ROLE_KEY` server-side only.
5. Install dependencies with `npm ci`, start with `npm run dev`, and build with `npm run build`.
6. Set the professor's published URL to the deployed app URL so QR codes point to the correct place.

## Rate limiter fix
The check-in Edge Function now allows up to **10 submissions per minute per (session code, student ID)**, instead of 5 attempts shared across a classroom. One student's submissions cannot consume another student's quota. This is a usability improvement, not a robust anti-abuse guarantee: student IDs are user-supplied, and concurrent requests can race during counting. For a production deployment, consider a database-atomic limiter and identity verification.

## Classroom smoke test
- Create professor account and course, upload roster, create session.
- Have 10 or more **different** students submit in one minute; no shared 429 should occur.
- Have the same student submit repeatedly; after 10 submissions in one minute, that student should get HTTP 429.
- Confirm roster mismatch is rejected and duplicate attendance is rejected.
- Verify records and student history after successful check-in.

**No live deployment or database test has been performed.** This archive provides updated source, not a guarantee that Bolt will deploy the function automatically.
