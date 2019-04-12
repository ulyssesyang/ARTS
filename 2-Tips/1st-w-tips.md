# When to use Git rebase and when to use Git merge

Today I saw a article of medium: [git — Rebase vs Merge](https://medium.com/datadriveninvestor/git-rebase-vs-merge-cc5199edd77c) suggests this: If the feature branch you are getting changes from is shared with other developers, rebasing is not recommended, because the rebasing process will create inconsistent repositories. For individuals, rebasing makes a lot of sense.

While I think it kind of inaccurate! Git rebase should be based on how complicated branch involve, should not be based on individuals.

I think if we work on one specific features and want to keep all comment histories clean, then I suggest using `Git rebase`, because git rebase will do all new features line up to exactly how the feature grows. Git rebase make perfectly sense in this case.

Another advance benefit when using `Git rebase` is `Git bisect`. `Git bisect` is used to track regression issues. So having a clean commit history defintely do great help on tracking down specific commit causing regression issues.

For `Git merge`, since it can merge any branch into target branch. So its usage case is definitely larger. For example, make master branch merge with other new features.

One thing for `Git merge` is DO GIT MERGE ONLY necessary! A lot of developer tends to merge master branches very often. This could be a bad practice, because `Git merge` will create merge commit each and also bring certain unnecessary new features which could break your current working branch.

Last, recommend a good article talking about git best practices in the Linux system: [Rebasing and merging: some git best practices](https://lwn.net/Articles/328436/). Quite interesting to see how such large project handling with git issues.