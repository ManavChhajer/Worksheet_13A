# Lab Learning Log: Command Line Utilities

## 1. System Logging Philosophies
A command like `log show` requires a fully functioning operating system and specific tools to decode a complex binary database, whereas plain text logs in `/var/log` remain permanently accessible and human-readable even if the primary logging system crashes. The `$PATH` variable dictates where the shell searches for program execution files (like `python3`), and tools like `wc -l` and Python list comprehensions can occasionally mismatch line counts if files lack proper trailing newline indicators or update mid-execution.

## 2. Command Line Shapes Used
- `grep -c "word" filename` (Counts instances of a string in a file)
- `ffmpeg -i input.mov -vf "scale=320:-1,fps=10" output.gif` (Processes and compresses media)
- `qrencode -o output.png "text"` (Generates a static QR code image)

## 3. Smallest Working Commands
- **To grep:** `grep "error" system.log`
- **To use ffmpeg:** `ffmpeg -i test.mov out.mp4`
- **To use qrencode:** `qrencode -o code.png "hello"`

## 4. Single Modifications Tested
- Modified `grep` by adding the `-c` flag to transform a string search into a purely numerical counter.
- Modified `ffmpeg` variables to dynamically adjust output frame rates (`fps=15`) and constrain dimension scaling (`scale=640:-1`).
- Modified `qrencode` payload strings to wrap dynamic URLs inside the text argument fields.

## 5. Intentional Breakage Results
- **Log File Check:** Running a script against a missing file throws a `FileNotFoundError`, letting you know the path reference is invalid.
- **FFmpeg Format Failure:** Appending an unparseable extension like `.xyz` causes `Unable to find a suitable output format`, proving ffmpeg maps container definitions strictly to file extensions.
- **FFmpeg Filter Error:** Mistyping a video filter tag (e.g., `sclae`) prints `Unknown filter`, demonstrating that the engine immediately drops execution if parameters miss registered methods.
- **Qrencode Missing Argument:** Omitting the output operator completely yields `no output file specified`, confirming the package treats destination paths as hard validation constraints.

## 6. Binary Tracking Rationale
Generated image assets like `.gif` and `.png` have been explicitly excluded from this remote tracking workflow. Git is intentionally optimized for tracking delta-based modifications in human-readable plain text documentation and code files; pushing blobs of raw binary compilation files forces performance overhead and artificially inflates repository size.