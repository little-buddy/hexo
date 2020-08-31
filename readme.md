# Little Buddy Hexo [![Netlify Status](https://api.netlify.com/api/v1/badges/07bf91b1-1d21-42d4-89ea-0a1ef5326223/deploy-status)](https://app.netlify.com/sites/obuddy/deploys)

```
git clone https://github.com/little-buddy/hexo.git
git submodule init && git submodule update

# 下面这一句效果和上面三条命令的效果是一样的，多加了个参数 "--recursive"
git clone https://github.com/little-buddy/hexo.git --recursive
```

## Netlify

```
Netlify's deployment infrastructure(基础设施) knows how to avoid uploading the same file twice,
even between different deploys, so we get your changes ready without duplicating content.


We've built Netlify's core around [Merkle trees], the same structures used in Git, ZFS file systems,
and blockchain technology.A Merkle tree is a structure where each node is labeled with the cryptographic
hash of the labels of all the nodes under it.

When we finish processing new deploys, we only swap the tree to serve.
Having immutable trees also prevents us from showing mixed content.

Another interesting advantage of immutable deploys is that we can point any name you want to any content you want.
This is the base for what we call Deploy Previews and Branch Deploys.

Can this be cached, and if so by whom?
    cache-control - private / public
How long can it be cached for
    cache-control - max-age
How can I tell if it's been changed?
    etag

通过设置 max-age=0 来使每次请求都不被缓存
然后通过 etag  a version hash来让服务器判断 hash是否变更而决定是否返回304来让浏览器读取本地缓存

you can override these caching settings with our custom headers feature
```

#### Definitions

```
- Production branch
    yoursitename.netlify.app
- Production deploy
    enabled, each new production deploy will update what is published at your site's main URL.
- Branch deploy
    a deploy generated from a branch that is not your production branch.
    deploy-url branchName--yoursitename.netlify.app
- deploy preview
    a deploy generated from a pull request or merge requests
    deploy-url deploy-preview-prNumber--yoursitename.netlify.app
```

### Deploy contexts

```
production
deploy-preview
branch-deploy
```

### File-based configuration

```
base = ""
publish = ""
comman = ""
```

### Netlify configuration variables

```
NODE_VERSION
NODE_ENV
NPM_VERSION
NPM_FLAGS
NPM_TOKEN               -> fetching private npm modules

YARN_VERSION            -> Yarn version
YARN_FLAG

RUBY_VERSION
PHP_VERSION
HUGO_VERSION
GO_VERSION
GO_IMPORT_PATH
AWS_LAMBDA_JS_RUNTIME
CI
GIT_LFS_ENABLED
GIT_LFS_FETCH_INCLUDE


预定义只读变量
NETFLIY
BUILD_ID
CONTEXT
_system_arch
_system_version

REPOSITORY_URL
BRANCH
HEAD
COMMIT_REF
CACHED_COMMIT_REF
PULL_REQUEST
REVIEW_ID

URL
DEPLOY_URL
DEPLOY_PRIME_URL
DEPLOY_ID
SITE_NAME
SITE_ID
NETLIFY_IMAGES_CDN_DOMAIN -> 构建过程中打开压缩才有效

INCOMING_HOOK_TITLE
INCOMING_HOOK_URL
INCOMING_HOOK_BODY
```
