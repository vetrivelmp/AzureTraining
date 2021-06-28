# Azure Storage Accounts - Azcopy tool

1. The download link - https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10

1. First create the shared access signature for your storage accounts

1.  To create a container, use the following command
```
azcopy make "https://saatin.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T08:58:33Z&st=2021-06-16T00:58:33Z&spr=https&sig=A%2FOQJ9i2fmsgTP3vVm8ajcMH3J%2F98ulQkvE9GlKWBA8%3D"
```

1. To upload a file, use the following command
```
touch Program.cs
azcopy copy Program.cs "https://saatin.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T08:58:33Z&st=2021-06-16T00:58:33Z&spr=https&sig=A%2FOQJ9i2fmsgTP3vVm8ajcMH3J%2F98ulQkvE9GlKWBA8%3D"
```


1. To upload a directory, use the following command
```
azcopy copy "newdir/*" "https://saatin.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T08:58:33Z&st=2021-06-16T00:58:33Z&spr=https&sig=A%2FOQJ9i2fmsgTP3vVm8ajcMH3J%2F98ulQkvE9GlKWBA8%3D"
```


1. To upload a directory to a directory in the container, use the following command
```
mkdir newdir
touch newdir/myProgram.cs
azcopy copy "newdir/*" "https://saatin.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T08:58:33Z&st=2021-06-16T00:58:33Z&spr=https&sig=A%2FOQJ9i2fmsgTP3vVm8ajcMH3J%2F98ulQkvE9GlKWBA8%3D"
```


1. To upload a directory and subdirectories to a directory in the container, use the following command
```
azcopy copy "newdir/*" "https://saatin.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T08:58:33Z&st=2021-06-16T00:58:33Z&spr=https&sig=A%2FOQJ9i2fmsgTP3vVm8ajcMH3J%2F98ulQkvE9GlKWBA8%3D" --recursive
```


1. To Download blob data, use the following command
```
azcopy copy --recursive "https://saatin.blob.core.windows.net/data/newdir/Program.cs?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T08:58:33Z&st=2021-06-16T00:58:33Z&spr=https&sig=A%2FOQJ9i2fmsgTP3vVm8ajcMH3J%2F98ulQkvE9GlKWBA8%3D" "Program.cs"
```

https://saatindest.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T09:20:17Z&st=2021-06-16T01:20:17Z&spr=https&sig=4d0wBrLM6o09y8Klqd%2BO0WjQOi3WnvauQbP%2FQvJi4I4%3D

1. To copy data between two storage accounts, use the following command
```
azcopy copy "https://saatin.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T08:58:33Z&st=2021-06-16T00:58:33Z&spr=https&sig=A%2FOQJ9i2fmsgTP3vVm8ajcMH3J%2F98ulQkvE9GlKWBA8%3D" "https://saatindest.blob.core.windows.net/data?sv=2020-02-10&ss=bfqt&srt=sco&sp=rwdlacuptfx&se=2021-06-16T09:20:17Z&st=2021-06-16T01:20:17Z&spr=https&sig=4d0wBrLM6o09y8Klqd%2BO0WjQOi3WnvauQbP%2FQvJi4I4%3D" --recursive
```
