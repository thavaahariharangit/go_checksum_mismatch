
In git lfs disabled module
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

lfs object uploaded to the same repo

```
hariharanthavachelvam@Hariharans-MacBook-Pro go_checksum_mismatch % git lfs track "*.zip" 
Tracking "*.zip"
hariharanthavachelvam@Hariharans-MacBook-Pro go_checksum_mismatch % git push                                          
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
hariharanthavachelvam@Hariharans-MacBook-Pro go_checksum_mismatch % 
```
