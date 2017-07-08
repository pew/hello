# docker v2 api calls

* [api spec](https://docs.docker.com/registry/spec/api/)

### get repositories

```
curl -sS -X GET https://registry.example.com/v2/_catalog                                                                                            
```

### list tags

```
curl -sS -X GET https://registry.example.com/v2/YOUR-REPO/tags/list
```

### get image digest

```
curl -I -X HEAD -H 'Accept: application/vnd.docker.distribution.manifest.v2+json' -sS https://registry.example.com/v2/YOUR-REPO/manifests/YOUR-TAG
```

**important**: for `HEAD` and `GET` requests, the header is important, [see here](https://docs.docker.com/registry/spec/api/#deleting-an-image)

> `Docker-Content-Digest: sha256: 111ef56b62b448284c0dd7a08b9f487337404a3d482d0182641a8c52552cf943`

### delete image

```
curl -sS -X DELETE https://registry.example.com/v2/YOUR-REPO/manifests/sha256:111ef56b62b448284c0dd7a08b9f487337404a3d482d0182641a8c52552cf943
```