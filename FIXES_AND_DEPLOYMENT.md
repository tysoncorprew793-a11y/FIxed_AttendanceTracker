# Attendance Tracker — repair notes

## Changes made
- QR links now show the check-in form even when the student is signed in; authentication is checked before choosing the screen.
- Offline check-ins are no longer presented as successful attendance. Local queued submissions are **not** official attendance.
- Queued check-in reconciliation does not repeatedly retry an already-recorded attendance response.
- Signup detects email-confirmation-required cases rather than trying to insert a profile without an authenticated session. **Important:** students who sign up with email confirmation enabled may still need a profile completion workflow after confirmation; this is not fully implemented.
- Added a safe additive SQL migration to support databases missing `checkin_attempts.student_id`.

## Required deployment steps
1. Back up the Supabase database before running SQL or deploying changes.
2. Run `supabase/migrations/20261119220000_repair_checkin_attempts_student_id.sql` in the SQL editor of the SAME database used by the published app. If earlier migrations were not applied, apply them in order with care.
3. Deploy `supabase/functions/checkin/index.ts` as the `checkin` Edge Function on that Supabase project. Check that `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` are available as server-side secrets. **Never** expose the service role key in the frontend.
4. Configure the frontend environment variables `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` (the public anon/publishable key) on the hosting platform. Do not commit secrets.
5. Run `npm ci` then `npm run build`, then deploy the resulting `dist` folder to a static host with SPA fallback (`/* /index.html 200`).
6. Test with a real professor session and two separate roster students, including an already signed-in student. Verify exactly one attendance record per student and that attempts by one student do not block another.
7. Confirm the published URL in professor settings so QR codes point to the deployed site.

## Known limitations
- No live Supabase database, secrets, or deployment access was provided. The ZIP alone cannot establish whether the live migration/function has been deployed.
- The offline queue is browser-local; queued submissions are not guaranteed to succeed or sync before session expiry. A professor should verify attendance.
- Signup when email confirmation is enabled needs an additional profile completion step after the student signs in.
- Role determination currently treats any authenticated user without a student profile as a professor. This should be hardened before production use with an explicit professor authorization table/role and secure onboarding.
