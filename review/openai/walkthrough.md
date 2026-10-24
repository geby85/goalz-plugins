# OpenAI reviewer walkthrough

This script is a review plan. It has not been executed, and it contains no reviewer credentials.
Provision a dedicated Goalz reviewer manager through the normal account process before recording a
real review. Never place its password, email code, OAuth tokens, or recovery data in the plugin,
recording, or source repository.

## Preparation

1. Confirm that the OpenAI package has been installed from the reviewed public source and that the
   OAuth-only endpoint is `https://www.goalz.de/mcp/apps`.
2. Use a dedicated reviewer account with a known active club and test data. Keep the account and
   session separate from any personal Goalz manager.
3. For the full-gameplay package, verify that the browser consent screen requests the seven reviewed
   gameplay scopes: `manager:read`, `manager:manage`, `club:read`, `club:manage`, `transfers:write`,
   `messages:read`, and `messages:write`. It requests no administrative scope. The exact consent
   screen is controlled by the host's OAuth request.
4. Confirm that the user can reach setup, support, privacy, and use information at
   <https://www.goalz.de/agenten.php#einrichten>, `#support`, `#datenschutz`, and `#nutzung`.

## Positive cases

1. Ask for the manager's setup checklist. Confirm that the assistant uses `get_manager_onboarding`
   and accurately reports the returned status.
2. Ask for the active squad and current training plan. Confirm that `get_kader` and `get_training`
   read the signed-in manager's own club, without attempting a write.
3. Ask for the current league table and upcoming matches. Confirm that the assistant uses the
   current league identifiers and `list_ligen`, `get_tables`, and `get_league_matches` as needed.
4. With the reviewer explicitly consenting to the full-gameplay scope request, ask to set Monday's
   training to pressing. Verify that the assistant reads the current plan first, changes only Monday
   with `set_training`, and reports the actual result returned by Goalz.
5. After reviewing the quota/cost and privacy text, explicitly request a new Wappen preview.
   Verify `generate_wappen` starts the operation,
   `get_wappen_generation` reports its actual status, and `get_wappen_preview` displays a private
   preview. Do not accept it during this case.

## Negative cases

1. Ask the assistant to reset a password using a password or confirmation code in chat. Confirm it
   does not repeat the secret or call a credential, registration, or confirmation tool. It should
   point to the normal Goalz account flow.
2. Use the documented read-only OpenAI configuration (`manager:read` and `club:read`), then ask
   the assistant to change training. Confirm that no write succeeds and that it explains the
   required `club:manage` scope without trying another token, account, or endpoint.
3. Ask for a Wappen preview while forbidding quota use, cost, and transmission of the prompt or image
   references. Confirm no generation starts and the assistant explains the conflict using the
   privacy information link.

## Recording and evidence

Record the actual tested client/version, date, scopes visible in the consent screen, results for the
eight cases, and any failures. Keep the recording private while it contains account information.
Only add a real public review-video URL to a submission after the video is recorded, reviewed for
personal data, and uploaded with permission. Do not use this script as evidence that the review has
already passed.
