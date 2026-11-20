# Contributing to Ejection Seat

Thanks for helping. This guide covers running Ejection Seat locally and sending a change.

## Where changes go

Ejection Seat is published in the [Raycast Store](https://www.raycast.com/chrismessina/ejection-seat).
Open pull requests against [`raycast/extensions`](https://github.com/raycast/extensions/tree/main/extensions/ejection-seat),
not this repository: Raycast reviews every change there, and merged changes come back here in a
sync pull request. Open [issues](https://github.com/chrismessina/raycast-ejection-seat/issues) here or in
`raycast/extensions`, whichever you prefer.

## Run it locally

You need [Raycast](https://www.raycast.com/) and Node.js 22.22.2 or later.

1. In Raycast, find Ejection Seat in the Store and choose **Fork Extension** from the action panel.
   Raycast checks out only this extension's folder from `raycast/extensions`.
2. In that folder, run `npm ci`, then `npm run dev`. Raycast opens the development version, and
   saving a file reloads it.

`npm test` runs `node --test` on TypeScript files directly, which needs Node.js 22.18 or later.

## Scripts

| Script | What it does |
| --- | --- |
| `npm run dev` | Run the extension in Raycast and reload on save |
| `npm run build` | Build the distribution bundle |
| `npm run lint` | Run Raycast's ESLint and Prettier checks |
| `npm run fix-lint` | Fix what the linter can fix |
| `npm test` | Run the parser tests in `tests/` |
| `npm run publish` | Open or update the pull request in `raycast/extensions` (`ray publish`) |
| `prepublishOnly` | Stops `npm publish`: the extension goes to the Raycast Store, never to the npm registry |

## How it works

The README's How It Works section describes the approach (`diskutil`, `mount`, `lsof`, `ps`). In
the code:

```
raycast-ejection-seat/
├── src/
│   ├── find-ejection-blockers.tsx    # The single command
│   └── disks.ts                      # Pure parsers for mount flags and disk layout
├── tests/                            # node --test fixtures for disks.ts
├── assets/                           # Extension icon (runtime)
├── media/                            # README images
├── metadata/                         # Store screenshots
├── package.json
└── tsconfig.json
```

## Before you open a pull request

- `npm run build`, `npx tsc --noEmit`, `npm run lint` and `npm test` all pass.
- You tried the change in Raycast, including its error and empty states.
- `CHANGELOG.md` has a new entry at the top, dated `{PR_MERGE_DATE}`. Raycast fills in the date
  when the pull request merges.
- New or changed screenshots go in `metadata/`, taken with Raycast's Window Capture.
