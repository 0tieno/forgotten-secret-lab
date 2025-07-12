# Forgotten Secret Lab: Hacking Git History
![Forgotten Secret Lab](https://example.com/lab-image.png)

Welcome to the Forgotten Secret Lab! 🕵️‍♂️

💡 Scenario:
> A developer accidentally committed a .env file containing a secret API key, then deleted it and added .env to .gitignore. But Git never forgets...

Your job is to investigate the commit history, uncover the secret, and use it to unlock a secret message from a live API.

## What You’ll Learn

✅ Real-world Git forensics
✅ Secret detection with open-source tools
✅ Recon & recovery from credential leaks
✅ How APIs can be abused when secrets leak
✅ Red-team & blue-team mindset

## Getting Started

```bash
git clone https://github.com/YOUR_USERNAME/forgotten-secret-lab.git
cd forgotten-secret-lab
```

🎯 Your Mission
Recover the deleted .env file from Git history and use the leaked API key to unlock a secret message.

✅ Objective:
- Hunt the secret inside Git history.
- Extract the key (looks like SECRET-TOKEN-1234)

🌐 Use it to query the secret API:

```bash
curl "https://forgottenSecretFunc12345.azurewebsites.net/api/data?key=SECRET-TOKEN-1234"
You should see:

```bash
{
  "message": "Congratulations! You've unlocked the secret."
}
```

🎉 Success! You found the leaked key and accessed the secret endpoint!

Wrong or missing key? You'll get:

```bash
{
  "error": "Invalid or missing key."
}
```

❌ Invalid or missing key. Try again.

## Helpful Git Commands

Tool	What it does
- git log -p	View commit history + diffs
- git show HEAD~1:.env	Show deleted file in earlier commit
- git grep "KEY" $(git rev-list --all)	Search all commits
- git cat-file -p <blob-sha>	View raw blob contents
- git log --diff-filter=D --summary	See deleted files
- gitleaks detect --source .	Detect secrets using rules
- trufflehog git file://./	Detect secrets via entropy
- git secrets --scan-history	Scan for common AWS/secret patterns

## Bonus Challenges
1. What’s the blob SHA of the deleted .env file?

2. What tool found the secret fastest?

3. Suggest one improvement to prevent this kind of leak in real-world teams.

4. Badge Earned
Complete this lab and you’ll earn the Git Forensics Hero badge on your SecureCloudX profile.

## Advanced: Track Who Solves It
We’ve set up the API to log:

- IP address

- Timestamp

- Request path

This lets us track completions and reward learners!

🔒 Don’t worry — it logs nothing sensitive, only what’s needed for leaderboard scoring.

🛡 Bonus Tips: Prevent This in Real Life

- Use .gitignore before committing sensitive files
- Add pre-commit hooks with git-secrets
- Set up GitHub secret scanning on your repos
- Use gitleaks in CI/CD pipelines

## Mindset Check

Mistakes happen. What matters is how you detect, contain, and respond.
Train to think like an attacker — and defend like a pro
