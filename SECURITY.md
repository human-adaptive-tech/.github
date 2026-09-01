# Security Policy

## Reporting a security problem

**Email Dr. Kunal Gupta at <kunal.gupta@auckland.ac.nz>.** Write "SECURITY" in the subject line.

**Do not open a public issue for a security problem.** That includes issues in private repositories, which are visible to everyone in the organisation. If you have already opened one, email as well rather than relying on it being noticed.

Please include what you found, how to reproduce it, what an attacker could do with it, and anything you have already tried. If you are not sure whether something counts, report it — a false alarm costs a few minutes.

The Studio is a small research group. We do not operate a formal disclosure programme, run a bug bounty, or guarantee a response time, and we would rather say so than imply otherwise. Expect an acknowledgement within a few working days, and follow up if you do not hear back.

## Exposed credentials

Never commit passwords, API keys, access tokens, certificates, private keys or production credentials.

Our current GitHub plan does not provide secret scanning or push protection on private repositories, so **nothing will detect a committed credential automatically**. Keep credentials in environment variables or a local `.env` file listed in `.gitignore`.

### If a credential is committed

Do these in order. The order matters.

1. **Rotate the credential immediately.** Revoke it and issue a new one. Do this before anything else and before telling anyone. Until the credential is dead, everything else is cosmetic.
2. **Tell the Organisation Owner**, and anyone else who uses that credential.
3. **Work out the exposure.** How long was it in the repository, who could see it, and was the repository ever public or shared with an outside collaborator? Check whether the service offers access logs for the period.
4. **Then deal with the history.** Removing the commit is the last step, not the first.

A credential that has been pushed must be treated as compromised even if the commit was deleted seconds later, and even if the repository is private. Deleting a file in a later commit does not remove it from Git history or from clones that already exist.

Nobody is in trouble for reporting this. People are in trouble for hiding it.

## Research data

Some material must never be in GitHub at all — participant-identifiable information, linkage files, consent forms, health information and raw participant recordings among them. If any of this reaches a repository, treat it as an incident and contact the Organisation Owner immediately, before attempting to fix it yourself.

Do not attempt to quietly delete it. What looks like a fix usually is not, and the response may have obligations attached that are not ours to judge alone. Institutional advice may be required, and it is better to seek it early.

**A private repository is not a data protection measure.** Do not rely on repository visibility to protect sensitive material.

Studio members: the full rules are in the internal handbook.

## Dependencies

- Prefer well-maintained dependencies, and add them deliberately rather than reflexively.
- Mention any new third-party dependency in your pull request, including its licence.
- Take dependency alerts seriously in anything that handles data or is deployed anywhere.
- Be careful with code copied from tutorials, forums or model output — it may carry licence obligations or known weaknesses.

## Scope

This policy covers repositories in the `human-adaptive-tech` organisation. Problems with GitHub itself go to GitHub. Problems with University systems go through the appropriate institutional channel; if you are unsure which, ask rather than guess.

**Contact:** Dr. Kunal Gupta — <kunal.gupta@auckland.ac.nz>
