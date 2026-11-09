# Changelog

## Unreleased

### Changed
- Requires `passport ^0.2` (the first published release of the core; `^0.1` matched no tag).

### Security
- Session files are named by the SHA-256 of the session ID, not the ID: reading the directory
  no longer gives live session IDs. Sessions stored before are not found (users log in
  again once).

### Added
- `filestore.New(dir)`: a `passport.SessionStore` keeping one file per session
  (`<id>.session`, mode 0600, in a directory with mode 0700), written atomically; expired
  sessions are removed when read, swept every 256 sessions and by `Cleanup`.
- Tests: the shared `sessionstoretest` suite, forged ids, file system errors, sweeping.
