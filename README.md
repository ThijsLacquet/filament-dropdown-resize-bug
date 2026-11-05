# Reproduction: dropdown closes on window resize (filters dropdown unusable on mobile)

Opening a Filament dropdown from its trigger makes it remember the `.fi-dropdown-trigger` wrapper
as its trigger, so the next window `resize` closes it. On a phone the on-screen keyboard resizes the
window, so tapping the search field of a filter inside the table's Filters dropdown closes the
dropdown (and the keyboard) straight away.

## Steps

1. `composer setup && php artisan serve`, log in at <http://127.0.0.1:8000/admin> with `test@example.com` / `password`.
2. Open **Users** and click the Filters (funnel) button.
3. Resize the browser window (or open DevTools docked at the bottom): the Filters dropdown closes.
4. On a phone (or Chrome DevTools device mode with a viewport height change): tap the **Users** filter's
   search field. The keyboard opens, and the Filters dropdown and the keyboard close at once.

The only code added on top of the template is `app/Filament/Resources/Users` (one searchable
`SelectFilter`) and 20 seeded users in `DatabaseSeeder`.

---

# Filament issue reproduction template

A minimal Laravel + Filament application for reproducing bugs you would like to file at [`filamentphp/filament`](https://github.com/filamentphp/filament/issues).

This repository is regenerated automatically from each stable Filament release. Each branch matches the Filament major version it was built against:

- [`3.x`](https://github.com/filamentphp/issue-reproduction-template/tree/3.x) — latest Filament v3 release (maintenance mode)
- [`4.x`](https://github.com/filamentphp/issue-reproduction-template/tree/4.x) — latest Filament v4 release
- [`5.x`](https://github.com/filamentphp/issue-reproduction-template/tree/5.x) — latest Filament v5 release

## Setup

You're on the `5.x` branch. To start a new reproduction project, run:

```bash
git clone --branch 5.x https://github.com/filamentphp/issue-reproduction-template.git filament-issue-reproduction
cd filament-issue-reproduction
composer setup
php artisan serve
```

`composer setup` installs Composer + npm dependencies, copies `.env.example` to `.env`, generates an app key, migrates and seeds the database, and builds frontend assets.

Log in at <http://127.0.0.1:8000/admin> with `test@example.com` / `password`.

Add the minimum code needed to reproduce your bug, push your repository, and link it from your Filament issue.
