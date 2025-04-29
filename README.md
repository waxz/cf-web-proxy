webproxy on cloudflare
# run 

```bash
DIR=$(pwd)
npm install wrangler --save-dev -C $DIR

npx -C $DIR wrangler pages dev  . --port 8888 --ip 0.0.0.0

# npx wrangler pages dev --local-protocol=https . --port 8888 --ip 0.0.0.0

# deploy to cloudflare
npx -C $DIR wrangler pages deploy
# npx -C $DIR wrangler pages deploy --project-name=my-proxy --branch=main --commit-dirty=true --commit-message="Manual deploy from $DIR"

```

# use d1
[making-static-sites-dynamic-with-cloudflare-d1](https://blog.cloudflare.com/making-static-sites-dynamic-with-cloudflare-d1/)
 
add permission 
- visit https://dash.cloudflare.com/profile/api-tokens
- select: account -> d1 -> edit

```bash
export CLOUDFLARE_API_TOKEN=xxxxx 
npx wrangler d1 create d1-example

npx  wrangler d1 execute d1-example --file src/create.sql
# upload to Pages
npx  wrangler d1 execute d1-example --remote  --file src/clean.sql
npx  wrangler d1 execute d1-example --remote  --file src/create.sql
```

