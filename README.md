# Sample Go Lang Repo
This repo is created to investigate Go Lang checksum mismatch between lfs-enabled and lfs-disabled repo.

## How to check checksum of a module
```terminal
$ go run github.com/vikyd/go-checksum@latest go.mod
file: go.mod
{
        "Hash": "8dd1839097bf0ab7ee6702280a8ee82f0fe39add5be8063bed8f8e57f697132e",
        "HashBase64": "jdGDkJe/CrfuZwIoCo7oLw/jmt1b6AY77Y+OV/aXEy4=",
        "HashSynthesized": "0abb0942c8dad296eb05063be387a90d5811536d1029c2494899d58ab421ed7b",
        "HashSynthesizedBase64": "CrsJQsja0pbrBQY744epDVgRU20QKcJJSJnVirQh7Xs=",
        "GoCheckSum": "h1:CrsJQsja0pbrBQY744epDVgRU20QKcJJSJnVirQh7Xs="
}
$ go run github.com/vikyd/go-checksum@latest . mynewmodule
directory: .
{
        "HashSynthesized": "d0c9b45a9de875534c550d1e9af17c50d3a97f488f79b39e094c8cfbf7716866",
        "HashSynthesizedBase64": "0Mm0Wp3odVNMVQ0emvF8UNOpf0iPebOeCUyM+/dxaGY=",
        "GoCheckSum": "h1:0Mm0Wp3odVNMVQ0emvF8UNOpf0iPebOeCUyM+/dxaGY="
}
```

## How to create the lfs enabled repo
```
$ git lfs track "*.zip" 
Tracking "*.zip"
$ git push                                          
Uploading LFS objects: 100% (1/1), 394 MB | 229 KB/s, done.                                                                                                                                                                                  
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 10 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 526 bytes | 526.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/thavaahariharangit/go_checksum_mismatch.git
   efd37ec..7afbc19  main -> main
```

## How to validate checksum in both lfs-enabled and lfs-disabled state

LFS-Disabled 
```terminal
go_checksum_mismatch % cd lfs-disabled 
lfs-disabled % source ~/.bash_profile
lfs-disabled % git clone https://github.com/thavaahariharangit/go_checksum_mismatch.git
Cloning into 'go_checksum_mismatch'...
remote: Enumerating objects: 44, done.
remote: Counting objects: 100% (44/44), done.
remote: Compressing objects: 100% (28/28), done.
remote: Total 44 (delta 16), reused 28 (delta 7), pack-reused 0
Receiving objects: 100% (44/44), 32.38 KiB | 1.25 MiB/s, done.
Resolving deltas: 100% (16/16), done.
hariharanthavachelvam@TL-WA854RE lfs-disabled % ls -1
go_checksum_mismatch
lfs-disabled % cd go_checksum_mismatch 
go_checksum_mismatch % go run github.com/vikyd/go-checksum@latest . mynewmodule
directory: .
{
	"HashSynthesized": "476b45f710fffd06d26d82f1855754f78af43022ce79077a106e61ee2905e749",
	"HashSynthesizedBase64": "R2tF9xD//QbSbYLxhVdU94r0MCLOeQd6EG5h7ikF50k=",
	"GoCheckSum": "h1:R2tF9xD//QbSbYLxhVdU94r0MCLOeQd6EG5h7ikF50k="
}
```

LFS-Enabled
```terminal
go_checksum_mismatch % cd lfs-enabled 
lfs-enabled % source ~/.bash_profile
lfs-enabled % GIT_LFS_SKIP_SMUDGE=1 git clone https://github.com/thavaahariharangit/go_checksum_mismatch.git
Cloning into 'go_checksum_mismatch'...
remote: Enumerating objects: 44, done.
remote: Counting objects: 100% (44/44), done.
remote: Compressing objects: 100% (28/28), done.
remote: Total 44 (delta 16), reused 28 (delta 7), pack-reused 0
Receiving objects: 100% (44/44), 32.38 KiB | 2.16 MiB/s, done.
Resolving deltas: 100% (16/16), done.
lfs-enabled % ls -1
go_checksum_mismatch
lfs-enabled % cd go_checksum_mismatch 
go_checksum_mismatch % git lfs pull
go_checksum_mismatch % go run github.com/vikyd/go-checksum@latest . mynewmodule
directory: .
{
	"HashSynthesized": "476b45f710fffd06d26d82f1855754f78af43022ce79077a106e61ee2905e749",
	"HashSynthesizedBase64": "R2tF9xD//QbSbYLxhVdU94r0MCLOeQd6EG5h7ikF50k=",
	"GoCheckSum": "h1:R2tF9xD//QbSbYLxhVdU94r0MCLOeQd6EG5h7ikF50k="
}
```



