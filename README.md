- 👋 Hi, I’m @Apr9637
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Apr9637/Apr9637 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
name: 'BrowserStack Test'
on: [push, pull_request]
jobs:
  ubuntu-job:
    name: 'BrowserStack Test on Ubuntu'
    runs-on: ubuntu-latest  # Can be self-hosted runner also
    steps:

      - name: 'BrowserStack Env Setup'  # Invokes the setup-env action
        uses: browserstack/github-actions/setup-env@master
        with:
          username:  ${{ secrets.BROWSERSTACK_USERNAME }}
          access-key: ${{ secrets.BROWSERSTACK_ACCESS_KEY }}

      - name: 'BrowserStack Local Tunnel Setup'  # Invokes the setup-local action
        uses: browserstack/github-actions/setup-local@master
        with:
          local-testing: start
          local-identifier: random

# The next 3 steps are for building the web application to be tested and starting the web server on the runner environment

      - name: 'Checkout the repository'
        uses: actions/checkout@v2

      - name: 'Building web application to be tested'
        run: npm install

      - name: 'Running application under test'
        run: ./node_modules/.bin/http-server -p 8099 &

      - name: 'Running test on BrowserStack'  # Invokes the actual test script that would run on BrowserStack browsers
        run: node index.js  # See sample test script above

      - name: 'BrowserStackLocal Stop'  # Terminating the BrowserStackLocal tunnel connection
        uses: browserstack/github-actions/setup-local@master
        with:
          local-testing: stop
 --->
