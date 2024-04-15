# omg CLI Release Notes
To install the latest omg cli updates, run `npm install -g @ombori/ga-cli` if you install it for the first time. You can also run `omg update` if you have already pre-installed omg package on your machine. 


## v3.91.4  (2024-04-15)
- Proxy support for all Phygrid (omg) CLI commands with network requests
  - To test, run `export HTTPS_PROXY=<proxy-url>` on the terminal
  - Execute commands like `omg org list`, `omg dev physhell <device-name>` and `omg dev status`
  - All Phygrid CLI requests should go through the set proxy

## v3.90.12 (2024-03-28)
- Increased inactivity timeout for `omg dev shell <device-name>` and other device streaming commands from 1minute to 5minutes

## v3.90.12 (2024-03-16)
- Increased inactivity timeout for `omg dev shell <device-name>` and other device streaming commands from 1minute to 5minutes


## v2.226.0 (2022-09-08)
- Added `--stage` parameter on `omg module publish` command. Valid stage values are `qa` and `production`

## v2.218.8 (2022-07-08)
- Overall optimization
  - from ~3-5seconds command response to ~0.5s

## v2.216.0 (2022-06-09)
- Improved app create initialization
- Fix app description command
- Updated screen, mobile, and IoT App templates to latest react and typescript versions
