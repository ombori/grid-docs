# omg CLI Release Notes
To install the latest omg cli updates, run `npm install -g @ombori/ga-cli` if you install it for the first time. You can also run `omg update` if you have already pre-installed omg package on your machine. 

## v3.92.11 (2024-05-29)
- fixed `phy app create <app-name>` error when creating screen app

## v3.92.2 (2024-05-16)
- brand new CLI with granular permissions and api endpoints under the hood
- introduced `phy` instead of `omg`. The `omg` prefix will still work for backward compatibility
- removed `omg dev physhell` command and make `omg dev shell` work for all types of devices (GridOS, Phyos, Tizen6.5 >)
- older versions of CLI will still work until June 30, 2024
  - run `omg update` to automatically download the new CLI

## v3.91.4  (2024-04-15)
- Proxy support for https requests and websocket connections
  - To test, run `export HTTPS_PROXY=<proxy-url>` on the terminal
  - Execute commands like `omg org list`, `omg dev physhell <device-name>` and `omg dev status`
  - All Phygrid CLI network requests should go through the configured proxy

## v3.91.4  (2024-04-15)
- Proxy support for https requests and websocket connections
  - To test, run `export HTTPS_PROXY=<proxy-url>` on the terminal
  - Execute commands like `omg org list`, `omg dev physhell <device-name>` and `omg dev status`
  - All Phygrid CLI network requests should go through the configured proxy

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
