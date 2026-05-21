Plan: Add Appointment Tab

TL;DR — Add a dedicated Appointment screen and bottom-navigation tab, move appointment-type reminders off the Home list into that new screen, and update navigation and UI. Filter appointments on the client to avoid Firestore query restrictions.

Steps
1. Create `lib/screens/appointment_screen.dart` — UI to list only appointment reminders (reuse HomeScreen card UI).
2. Update `lib/screens/home_screen.dart` — filter out appointment reminders when building the reminders list (client-side filter).
3. Update `lib/main.dart`:
   - Insert `AppointmentScreen` into the `screens` list.
   - Add a BottomNavigationBar item for Appointment (adjust indices and selected behavior).
4. Run app, test navigation and that appointments appear only in the Appointment tab and not in Home.
5. Optional: update docs and add a small widget-test verifying the appointment filter.

Relevant files
- `lib/main.dart` — modify `AppShell` screens list and BottomNavigationBar items.
- `lib/screens/home_screen.dart` — change stream handling to filter out appointments.
- `lib/screens/appointment_screen.dart` — new file to implement appointment list UI.

Verification
1. `flutter analyze` — no analyzer errors.
2. `flutter run -d <device>` — app launches and shows new Appointment tab.
3. Create test appointment documents in Firestore with `category: 'appointment'` and verify:
   - They appear only under the Appointment tab.
   - Home tab shows non-appointment reminders.
4. Manual UI checks: bottom nav selection, back navigation, snackbars for empty list.

Decisions
- Filter appointments client-side (safer and avoids Firestore inequality indexing).
- Reuse existing card UI from `HomeScreen` for visual consistency.
- Keep bottom navigation; adding one more tab (total 5) is within Material guidelines.

Further Considerations
1. If Firestore dataset grows, consider server-side queries with proper indexes or separate collections.
2. If bottom-nav becomes crowded later, consider using a drawer or a segmented home layout.
