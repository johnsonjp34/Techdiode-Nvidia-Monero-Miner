# Techdiode Nvidia Monero Miner.
This is a fork from XMRig. XMRig is high performance Monero (XMR) NVIDIA miner.

GPU mining part based on [psychocrypt](https://github.com/psychocrypt) code used in xmr-stak-nvidia.

* This is the NVIDIA GPU mining version.

For release binaries see release tab. https://github.com/johnsonjp34/Techdiode-Nvidia-Monero-Miner/releases

# ANTIVIRUS - The Monero opensource code gets flagged by ANTIVIRUS software because of all the hacker trolls embeding the code everywhere to steal your processing power. You will need to add an exception to your antivirus and browser. If you don't, especially on Windows, your executable will disappear from time to time by the hands of Windows Defender.

See Dependencies folder extras needed for building. 
You will need to build:

the Cuda Toolkit 8.

CMake 64 

make a build directory in your project. cd into it and do:
```` cmake .. -G "Visual Studio 15 2017 Win64" -T v140,host=x64 -DUV_INCLUDE_DIR="c:\<path>\msvc2015\libuv\x64\include" -DUV_LIBRARY="c:\<path>\msvc2015\libuv\x64\lib\libuv.lib" -DMHD_INCLUDE_DIR="c:\<path>\msvc2015\libmicrohttpd\x64\include" -DMHD_LIBRARY="c:\<path>\msvc2015\libmicrohttpd\x64\lib\libmicrohttpd.lib" ````
-make sure you change the path to where you have downloaded the deps folder

## Features
* High performance.
* Official Windows support.
* Support for backup (failover) mining server.
* CryptoNight-Lite support for AEON.
* Automatic GPU configuration.
* GPU health monitoring (clocks, power, temperature, fan speed) 
* Nicehash support.
* It's open source software.



## Usage

### Command line options
```
  -a, --algo=ALGO         cryptonight (default) or cryptonight-lite
  -o, --url=URL           URL of mining server
  -O, --userpass=U:P      username:password pair for mining server
  -u, --user=USERNAME     username for mining server
  -p, --pass=PASSWORD     password for mining server
  -k, --keepalive         send keepalived for prevent timeout (need pool support)
  -r, --retries=N         number of times to retry before switch to backup server (default: 5)
  -R, --retry-pause=N     time to pause between retries (default: 5)
      --no-color          disable colored output
      --donate-level=N    donate level, default 5% (5 minutes in 100 minutes)
      --user-agent        set custom user-agent string for pool
  -B, --background        run the miner in the background
  -c, --config=FILE       load a JSON-format configuration file
  -l, --log-file=FILE     log all output to a file
      --nicehash          enable nicehash support
      --print-time=N      print hashrate report every N seconds
  -h, --help              display this help and exit
  -V, --version           output version information and exit

Auto-configuration specific options:
      --bfactor=[0-12]    run CryptoNight core kernel in smaller pieces
                          from 0 (ui freeze) to 12 (smooth), Windows default is 6
      --bsleep=N          insert a delay of N microseconds between kernel launches
      --max-gpu-threads=N limit maximum count of GPU threads
```

### Config file.
GPU configuration now possible only via config file. Sample config:
```json
{
    "background": false,
    "colors": true,
    "donate-level": 5,
    "log-file": null,
    "print-time": 60,
    "retries": 5,
    "retry-pause": 5,
    "syslog": false,
    "threads": [
        {
            "index": 0,
            "threads": 42,
            "blocks": 18,
            "bfactor": 6,
            "bsleep": 25
        }
    ],
    "pools": [
        {
            "url": "pool.minemonero.pro:5555",
            "user": "",
            "pass": "x",
            "keepalive": true,
            "nicehash": false
        }
    ]
}
```
If `threads` option not specified the miner will try automatically create optimal configuration for your GPUs.

## Donations
Default donation 1% (1 minutes in 100 minutes) goes to 5% if you try to make it lower. You can override if you build it yourself.

