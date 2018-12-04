# Dot files

## Git

### copy history of files to the separate repo

#### create a patch for files

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
