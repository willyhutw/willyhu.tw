# willyhu.tw

## Create post and publish the site

```bash
cd willyhu.tw

# Create and edit a new post
hugo new posts/new-post.md
vim content/posts/new-post.md

# Re-generate whole site in public/
hugo

# build container image
buildah build -f docker/Dockerfile -t public.ecr.aws/${registry-alias}/willyhutw:${version}

# login aws ecr
aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/${registry-alias}

# push container image to aws ecr
buildah push public.ecr.aws/${registry-alias}/willyhutw:${version}
```