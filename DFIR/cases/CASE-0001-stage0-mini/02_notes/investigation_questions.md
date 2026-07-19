# Investigation questions

| ID | Question | Priority | Required evidence | Status | Answer / finding |
|---|---|---|---|---|---|
| Q-01 | Which files contain confidential information? | High | File contents | Closed | `review_note.txt` and `review_note_copy.txt` contain sensitive Project Nightjar details; `meeting_notes.txt` does not. |
| Q-02 | Are any files exact duplicates? | Medium | SHA-256 hashes, cmp/diff output | Closed | Yes, `review_note.txt` and `review_note_copy.txt` are byte-by-byte identical. |
| Q-03 | Can the available evidence establish which file was created first? | Medium | Timestamp analysis, metadata | Closed | No, standalone text exports lack the metadata/audit logs needed to determine creation order. |
| Q-04 | Can the available evidence identify who created or copied the files? | Medium | Access logs, user identifiers | Closed | No, there is no attribution metadata or system logs to link file activity to a specific person. |
