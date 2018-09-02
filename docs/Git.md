##Remove untracked files git
Show what will be deleted with the -n option:
```bash
git clean -f -n
```
Then - _beware_: this will delete files - run:
```bash
git clean -f
```
If you want to also remove directories, run
```bash
git clean -fd
```
If you just want to remove ignored files, run
```bash
git clean -fX
```
If you want to remove ignored as well as non-ignored files, run
```bash
git clean -fx
```
**_Note_** the case difference on the X for the two prev commands.
If `clean.requireForce` is set to `true` (the default) in your configuration, then unless you specify -f nothing will actually happen.
See the `git-clean` docs for more information.