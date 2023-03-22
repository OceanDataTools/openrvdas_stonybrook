# Seawolf Meta-HowTo 2023-03-22

Please check this repository out of GitHub somewhere (on Linux or
MacOS the convention is into /opt/oceandatatools_local/stonybrook).
Then create a symlink from stonybrook to the `local` subdir of the
OpenRVDAS installation you want to use it with. E.g.
```
  ln -s /opt/oceandatatools_local/stonybrook /opt/openrvdas/local/stonybrook
```

# Seawolf HowTo 2019-12-09
David Pablo Cohn

## Installation

 * Install Python v3.7 via Anaconda
 * Install Git from https://git-scm.com/download/win
 * Inside Anaconda CMD prompt:
    * pip install pyserial websockets PyYAML parse
    * cd <directory where you want to install OpenRVDAS>
    * git clone https://github.com/oceandatatools/openrvdas.git
    * git checkout stonybrook

From there, you should be able to run the basic OpenRVDAS commands below.

```
   python logger\listener\listen.py --config_file local\stonybrook\seawolf.yaml:met1_on
```

## To run with cached data server

In one terminal:
```
   python logger\listener\listen.py --config_file local\stonybrook\seawolf.yaml:met1_cache
```
In another:
```
   python server\cached_data_server --port 8766
```
Should then be able to see live met data from cached data server via:
```
   python logger\listener\listen.py --cached_data Met1WindDirTrue,Met1WindSpeedKt@localhost:8766
```
 Or view the data in a demo HTML page by opening the page at
   display\html\seawolf_demo.html
