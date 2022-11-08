# EUM Simulator Next Generation

## The Old Way

The previous EUM simulation is made up of a number of a rat's nest of interconnected applications. The main user load is generated by running Chrome under the control of puppeteer inside a Nodejs application. To achieve sufficient load 3 replicas have to be run taking a total of 3GB memeory and a lot of CPU. All that resource usage and it only provides 2 pages for browser and one view for mobile.

## Next Generation

Taking a much lighter weight approach, the next generation uses template beacons captured from the agent, makes calls to the backend to get the correlation ID `munges` the beacon then sends it to the backend. The sequence of pages, ajax calls, errors and page transitions is all configured via a configuration file e.g.  `config-shop.js`. See comments inline for details. The configuration file to use is set via the `CONFIG` environment variable.

The next gen eum simulator performs two roles simultaneously, first of all it generates EUM beacons and sends them to the backend, second it provides the front end endpoints to service the requests. The front end is Expressjs which is dynamically configured from the configuration file. The front end application will also capture and store the template beacons when exercised by a real browser.

# How To Run Simulator

* Run `npm install`
* Start simulator, by default simulator uses configuration `config-shop.js`, to use `config-test.js` add `t` argument 
  * locally `./run.sh -f` or `./run.sh -ft`
  * in docker `./run.sh -br` or `./run.sh -brt`

## Work In Progress

### To Do

* Make the port number fully configurable. At the moment `8000` is hard coded in a number of places.

