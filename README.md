# auto-green

[![Build Status](https://github.com/bebestmaple/auto-green/workflows/ci/badge.svg?branch=main)](https://github.com/bebestmaple/auto-green/actions)

Automatically keep your GitHub contribution graph green.

> a commit a day keeps your girlfriend away.

## How it works

This project uses GitHub Actions scheduled workflows to automatically execute `git commit` once per day. The commit message is "a commit a day keeps your girlfriend away", inspired by an anonymous answer to the Zhihu question [What's it like to keep your GitHub contribution graph green for 365 days?](https://www.zhihu.com/question/34043434/answer/57826281):

> I kept it green for over 200 days, but I neglected my girlfriend, and I've been green ever since.

For more information about GitHub Actions, see the official documentation [Introduction to GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions).

## Usage

- Click the **Use this template** button in the top right to copy this GitHub repository. **:warning: Do NOT Fork, because fork activity won't make your contribution graph green :warning:**
- Modify [lines 23-24 in ci.yml](https://github.com/hungdinhxuan/auto-green/blob/master/.github/workflows/ci.yml#L23-L24) to set your GitHub email and name
- (Optional) You can adjust the schedule by modifying [line 8 in ci.yml](https://github.com/hungdinhxuan/auto-green/blob/master/.github/workflows/ci.yml#L8)

The cron schedule syntax has 5 fields, separated by spaces, each representing a time unit.

```plain
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of month (1 - 31)
│ │ │ ┌───────────── month (1 - 12 or JAN-DEC)
│ │ │ │ ┌───────────── day of week (0 - 6 or SUN-SAT)
│ │ │ │ │
│ │ │ │ │
│ │ │ │ │
* * * * *
```

Meaning of each time field:

| Symbol | Description | Example |
| ------ | ----------- | ------- |
| `*` | Any value | `* * * * *` every minute of every hour of every day |
| `,` | Value separator | `1,3,4,7 * * * *` at minutes 1, 3, 4, and 7 of every hour |
| `-` | Range | `1-6 * * * *` at minutes 1-6 of every hour |
| `/` | Every | `*/15 * * * *` every 15 minutes |

**Note**: Due to GitHub Actions limitations, if you set `* * * * *`, the actual execution frequency will be once every 5 minutes.

The default schedule is `0 0 * * *`, which runs once daily at midnight UTC.

## License

[auto-green](https://github.com/hungdinhxuan/auto-green) is released under the MIT License. See the bundled [LICENSE](./LICENSE) file for details.
