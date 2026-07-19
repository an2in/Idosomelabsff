# Technical report

## 1. Purpose and investigation questions

The purpose of this investigation is to examine three supplied text files, identify files containing restricted information, determine whether any files are exact duplicates, and document the limitations of the available evidence.

The investigation is guided by four core questions:
- **Q-01**: Which files contain restricted information?
- **Q-02**: Are any files exact duplicates?
- **Q-03**: Can the available evidence establish which file was created first?
- **Q-04**: Can the available evidence identify who created or copied the files?

## 2. Evidence received

Three evidence items were received by the investigator on 2026-07-18. Integrity was verified via SHA-256 hashing during intake on 2026-07-19:

- **E-001** (`meeting_notes.txt`): Size 126 bytes. SHA-256: `600812adbf83a72d613dd6447a10e848fec222b6a8e89bf6f39f66439571946f`.
- **E-002** (`review_note_copy.txt`): Size 152 bytes. SHA-256: `62257dd5a11fd4849723ff768fae875452c51d8adaf9d44e5deb8b5cb9866f48`.
- **E-003** (`review_note.txt`): Size 152 bytes. SHA-256: `62257dd5a11fd4849723ff768fae875452c51d8adaf9d44e5deb8b5cb9866f48`.

Analysis was performed on verified working copies, and no intentional modifications were made to the original evidence. Hashing operations updated the filesystem access times but did not modify file contents.

## 3. Methodology

The forensic analysis followed a systematic, four-step process:
1. **Integrity Check**: Calculated and recorded SHA-256 hashes of the files upon intake to establish a cryptographic baseline.
2. **Text Analysis**: Conducted targeted keyword searches across the working copies to locate mentions of sensitive project names or distribution markers (e.g., "Project Nightjar").
3. **Duplicate Comparison**: Performed byte-by-byte file comparisons using system utilities (`cmp` and `diff`) and compared SHA-256 hashes to confirm exact content equivalence.
4. **Metadata & Attribution Review**: Analyzed filesystem metadata (modification, access, and change timestamps) and contrasted it with dates written inside the file contents to assess temporal and attribution limitations.

## 4. Findings

The following findings were registered during the analysis:

- **F-001 (Restricted Information Identified)**: The files `review_note.txt` (E-003) and `review_note_copy.txt` (E-002) contain Project Nightjar information explicitly marked for restricted distribution (limited to the project lead and security reviewer). In contrast, `meeting_notes.txt` (E-001) does not contain references to Project Nightjar or language restricting its distribution.
- **F-002 (Exact Content Duplication)**: A byte-by-byte comparison and identical SHA-256 hashes confirm that `review_note.txt` and `review_note_copy.txt` contain identical byte sequences. However, this only proves duplicate content and does not establish which file was the original source or how the duplication occurred.
- **F-003 (Attribution and Creation Order Limits)**: The available evidence is insufficient to establish which duplicate file existed first, or who was responsible for creating or copying them. Standalone text exports do not contain author fields, and the available filesystem metadata may reflect copying, export, extraction, or storage on the investigator’s filesystem rather than the original creation events.

## 5. Conclusion and limitations

Based on the evidence, the investigation concludes the following:
- **Which files contain restricted information?** The files `review_note.txt` and `review_note_copy.txt` contain Project Nightjar information explicitly marked for restricted distribution, while `meeting_notes.txt` does not.
- **Are any files exact duplicates?** Yes, `review_note.txt` and `review_note_copy.txt` are exact byte-for-byte duplicates sharing the identical SHA-256 hash.
- **Which file existed first?** The available evidence cannot establish which duplicate existed first, as filesystem modification timestamps may reflect export or copying events rather than original creation.
- **Who created or copied them?** The available evidence cannot identify who created or copied the files because the evidence set lacks system access logs, user account information, or other attribution metadata.

### Limitations of the Investigation
1. **Export-altered Metadata**: The filesystem modification timestamps of all three files are identical (`2026-07-18 06:00:24`). The identical modification timestamps are consistent with a shared copying or export event, but they do not establish when the original documents were created.
2. **Lack of File Format Metadata**: Plain text files (.txt) do not support internal metadata tags (such as author, creator, or creation history) that are common in richer document formats.
3. **Absence of OS Artifacts**: No operating-system event logs, shell histories, original filesystem metadata, NTFS $MFT records, or $UsnJrnl entries were provided, preventing reconstruction of user activity or file-copy history.
