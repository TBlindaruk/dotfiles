# Dot files

## Git

### Copy history of files to the separate repo

#### Create a patch for files

```bash
$ git log --pretty=email --patch-with-stat --reverse --full-index --binary -m --first-parent  -- ${1}> "${2}"
```

<strong> example: </strong>

```bash
$ git log --pretty=email --patch-with-stat --reverse --full-index --binary -m --first-parent  -- src/Illuminate/Notifications/Messages/SlackMessage.php src/Illuminate/Notifications/Messages/SlackAttachment.php > "../_patch"
```

<i>Notice:</i>
```bash
-m --first-parent
```
You should not use it in case if it possible

#### apply patch 

```bash
$ git am --committer-date-is-author-date   < ../_patch

```

#### Links:

- https://stackoverflow.com/questions/1365541/how-to-move-files-from-one-git-repo-to-another-not-a-clone-preserving-history/11426261#11426261
- https://gist.github.com/tsayen/f1c1c4d62d4fda77abf1586bd39f9b74

### Copy history of the directory to the separate repository

TODO: http://gbayer.com/development/moving-files-from-one-git-repository-to-another-preserving-history/
TODO: https://gist.github.com/whistler/de34b77aba2221ed8b2e


### Git blame

```bash
$ git ls-files -z | xargs -0n1 git blame -w | perl -n -e '/^.*\((.*?)\s*[\d]{4}/; print $1,"\n"' | sort -f | uniq -c | sort -n
```

