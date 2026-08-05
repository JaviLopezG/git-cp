# git cp

This is a git extension that copy a file with its whole history.

You can look at file-original and file-cloned to understand what can you expect from this script.

## How to use
```
git cp original cloned
```

"original" must be an existing file with history in the current repository.

## How to analyze results
```
git log --follow original #follow shows the whole history if the file was moved at some point
git log cloned
```

For the commits of Renames (`git mv`) set with status R when you look the raw log with (`git log --raw`) there are no file modifications so you can't add changes to tje commit. My solution (there are other possible solutions) was add a white space at the end of the file. If the Rename is not the last commit, the white space will be removed when the content was recovered from the database for the next commit. If it is the last one, the white space will persist.

You can check this case if you show white spaces in files.
```
cat file-original | tr " " "_"
cat file-cloned | tr " " "_"
```

# How to install
You only need to add the script to a directory in the PATH. For instance:
```
sudo cp git-cp /bin/bash
```

You can also use it from repo directory using the full name
```
~/my-repos/git-cp original cloned
```
 



