<picture>
  <source media="(prefers-color-scheme: dark)" srcset=".github/assets/readme-header-dark.png">
  <img alt="kwtSMS: SMS gateway for Kuwait" src=".github/assets/readme-header-light.png">
</picture>

# kwtSMS for Moodle

[![Moodle Plugins Directory](https://img.shields.io/badge/Moodle.org-local__kwtsms-orange.svg)](https://moodle.org/plugins/local_kwtsms)
[![Moodle](https://img.shields.io/badge/Moodle-4.3+-orange.svg)](https://moodle.org)
[![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4.svg)](https://www.php.net)
[![Release](https://img.shields.io/github/v/release/kwtsms/moodle-local_kwtsms)](https://github.com/kwtsms/moodle-local_kwtsms/releases)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

Send SMS to your students when they enrol, get a grade, submit work or complete a course, and to your admins when a
new user registers, through kwtSMS, the Kuwaiti SMS gateway.

kwtSMS delivers to Zain, Ooredoo, stc and Virgin in Kuwait and to more than 200 countries, with your own Sender ID,
free API testing and credits that do not expire.

## Features

**Notifications**
- Seven Moodle events: enrolment, unenrolment, grade posted, course completed, quiz submitted, assignment submitted,
  and new user registered (to admin phones).
- English and Arabic templates with placeholders such as `{firstname}`, `{coursename}` and `{grade}`.

**Admin**
- One admin page with seven tabs: Dashboard, Settings, Gateway, Templates, Integrations, Logs and Help.
- Balance, Sender IDs and coverage synced daily, with a low balance alert.
- Message log with phone masking, filters and CSV export.
- Test mode: messages are queued on kwtSMS and not delivered.
- Right-to-left layout for Arabic.

## Requirements

- Moodle 4.3 or later, PHP 8.1 or later, PostgreSQL or MariaDB/MySQL.
- A kwtSMS account (free test account, no papers): https://www.kwtsms.com/cportal/signup/

### Tested versions

Every push runs the Moodle Plugin CI across the full matrix below. All jobs green as of v1.0.2.

| Moodle | PHP | Database |
|--------|-----|----------|
| 4.3    | 8.1 | PostgreSQL |
| 4.4    | 8.1 | MariaDB |
| 4.5    | 8.2 | PostgreSQL |
| 4.5    | 8.3 | MariaDB |
| 5.0    | 8.2 | PostgreSQL |
| 5.1    | 8.3 | MariaDB |
| 5.2    | 8.3 | PostgreSQL |

## Installation

Pick whichever option suits your workflow. All three install the same version.

### Option 1: Install from Moodle.org (recommended)

1. Sign in to your Moodle site as an administrator.
2. Go to **Site administration > Plugins > Install plugins**.
3. Click **Install plugins from the Moodle plugins directory**.
4. Search for `kwtSMS` or go to https://moodle.org/plugins/local_kwtsms.
5. Click **Install now** and follow the prompts.

### Option 2: Upload a ZIP

1. Download the latest release ZIP from the
   [GitHub releases page](https://github.com/kwtsms/moodle-local_kwtsms/releases)
   or from the [Moodle plugins directory](https://moodle.org/plugins/local_kwtsms).
2. In Moodle, go to **Site administration > Plugins > Install plugins**.
3. Drag the ZIP into the installer and click **Install plugin from the ZIP file**.
4. Follow the prompts to complete the upgrade.

### Option 3: Install from source

1. Clone or extract the plugin into `local/kwtsms/` under your Moodle directory:
   ```bash
   git clone https://github.com/kwtsms/moodle-local_kwtsms.git local/kwtsms
   ```
2. Visit **Site administration > Notifications** to complete the installation.

### After installing

1. Go to **Site administration > Plugins > Local plugins > kwtSMS**.
2. Open the **Gateway** tab and log in with your kwtSMS API credentials.

## Setup

1. Go to **Site administration > Plugins > Local plugins > kwtSMS**.
2. **Gateway** tab: enter the API username and password of your kwtSMS account (not your mobile number), click
   **Login**, then choose your Sender ID and default country code.
3. **Settings** tab: enable the gateway, turn on test mode for a first try, add admin phone numbers and the low balance
   threshold.
4. **Integrations** tab: choose the events that send SMS.
5. **Templates** tab: adjust the English and Arabic messages.

Test mode messages are not delivered, but their credits are held until you delete them from the Sending Queue in your
kwtSMS account.

## Supported Events

| Event | Recipient | Description |
|-------|-----------|-------------|
| User Enrolled | Student | Sent when a user is enrolled in a course |
| User Unenrolled | Student | Sent when a user is removed from a course |
| Grade Posted | Student | Sent when a grade is published |
| Course Completed | Student | Sent when a user completes a course |
| Quiz Submitted | Student | Sent when a quiz attempt is submitted |
| Assignment Submitted | Student | Sent when an assignment file is uploaded |
| New User Registered | Admin | Sent to admin phones when a new user registers |

## Template Placeholders

| Placeholder | Available In | Description |
|-------------|-------------|-------------|
| `{firstname}` | All events | User's first name |
| `{lastname}` | All events | User's last name |
| `{coursename}` | Course events | Course full name |
| `{grade}` | Grade Posted | The grade value |
| `{activityname}` | Quiz/Assignment | Activity name |
| `{sitename}` | All events | Moodle site name |

## Arabic

The plugin interface and every template are available in Arabic, with a right-to-left layout. Arabic SMS are sent as
Unicode: one SMS page holds 70 Arabic characters, against 160 English ones.

## FAQ

**Which username do I use?** The API username and password of your kwtSMS account, not your mobile number.

**Why do test messages not arrive?** Test mode queues messages without delivering them. Turn it off in Settings.

**What is a Sender ID?** The name shown as the sender on the phone. `KWT-SMS` is a shared test Sender ID; for real
messages register your own. See the [Sender ID help](https://www.kwtsms.com/sender-id-help.html).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## Support

Help: https://www.kwtsms.com/support.html | FAQ: https://www.kwtsms.com/faq/ |
API: [developers](https://www.kwtsms.com/developers.html), [API reference](https://www.kwtsms.com/api-documentation.html) |
[Issues](https://github.com/kwtsms/moodle-local_kwtsms/issues)

## Security

See [SECURITY.md](SECURITY.md).

## License

GNU GPL v3 or later, (c) kwtSMS (BoxLink Center). See https://www.gnu.org/copyleft/gpl.html.
