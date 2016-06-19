# http_load

http_load - multiprocessing http test client  
version of 12, mar, 2006

http://www.acme.com/software/http_load/

http_load runs multiple http fetches in parallel, to test the
throughput of a web server.  However unlike most such test clients,
it runs in a single process, so it doesn't bog down the client
machine.  It can be configured to do https fetches as well.

See the manual entry for more details.

Files in this distribution:

    README          this
    Makefile        guess
    http_load.c     source file
    http_load.1     manual entry
    timers.c        timers package
    timers.h        headers for timers package
    make_test_files simple script to create a set of test files

To build: If you're on a SysV-like machine (which includes old Linux systems
but not new Linux systems), edit the Makefile and uncomment the SYSV_LIBS
line.  If you're doing SSL, uncomment those lines too.  Otherwise, just do
a make.

Feedback is welcome - send bug reports, enhancements, checks, money
orders, etc. to the addresses below.  
[Jef Poskanzer](jef@mail.acme.com)   
<http://www.acme.com/jef/>

***
We modified the http_load to making it demonstrates the percentage distribution of response time. Like:

    $ http_load -r 100 -s 60 urls

    5997 fetches, 24 max parallel, 2.79964e+07 bytes, in 60 seconds
    4668.4 mean bytes/connection
    99.95 fetches/sec, 466607 bytes/sec
    msecs/connect: 4.76659 mean, 1256.03 max, 1.55 min
    msecs/first-response: 27.1605 mean, 313.85 max, 6.724 min
    5976 bad byte counts
    HTTP response codes:
      code 200 -- 5997

    Percentage of the requests served within a certain time (ms)
     50%    22
     66%    25
     75%    27
     80%    29 
     90%    37 (90% of response time is less than 37 ms)
     95%    51
     98%    73
     99%    93
     100%   313 (longest request)
