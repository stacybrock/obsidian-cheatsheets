# MDE on macOS sadness

## telemetryd_v2 badness
- [Troubleshoot performance issues for Microsoft Defender for Endpoint on macOS](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/mac-support-perf?view=o365-worldwide)

To search for processes that cause performance issues in MDE (lol), enable real-time protection and real-time protection statistics gathering and read the output like tea leaves...

1. Enable real-time protection & stats gathering.
```
$ mdatp config real-time-protection --value enabled
$ mdatp config real-time-protection-statistics  --value enabled
```
2. Let the stat gathering run for a while, preferably while the poor performance is observed.
3. Capture statistics.
```
$ mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
```
4. Analyze the results.
```
$ jq '.counters | sort_by(.total_files_scanned) | reverse[] | {name,id,total_files_scanned,path}' real_time_protection.json
```
The output of the above is a list of the top contributors to performance issues. Included is the process name, PID, total number of scanned files (since stats gathering was started, resets upon reboot), and process path, sorted by impact.

5. Based on results, add exclusions for processes too mighty for MDE to handle. See: [Configure and validate exclusions for Microsoft Defender for Endpoint on Linux](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-exclusions?view=o365-worldwide)
