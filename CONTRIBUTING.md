# Updating from puppeteer

This is a messy process because we aren't yet maintaining a proper fork of
puppeteer but are instead working with a built version. This means that we can't
just "merge upstream" and instead have to manually reconcile changes.

1. Create a merge branch based on the last update source commit
   ```sh
   git fetch origin
   git checkout <sha of last update commit>
   git checkout -b merge/1.20.0
   ```
2. Clone https://github.com/puppeteer/puppeteer and checkout target release tag
   ```sh
   cd ..
   git clone git@github.com:puppeteer/puppeteer g-puppeteer
   git checkout v1.20.0
   ```
3. Install and build
   ```sh
   cd g-puppeteer
   npm i
   npm run build
   ```
4. Copy new sources to this clone
   ```sh
   cp -R ./{lib,*.js,*.json} ../puppeteer
   ```
5. Commit the update
   ```sh
   cd ../puppeteer
   git add .
   git commit -m 'Update to v1.20.0'
   ```
6. Merge in main and resolve any conflicts. Be sure to update the package.json
   to use `@recordreplay/puppeteer` as the name and the new version.
   ```sh
   git merge origin/main
   ```
7. Push and open a PR