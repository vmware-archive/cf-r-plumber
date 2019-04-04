[Plumber API Example](https://www.rplumber.io/), slightly modified to run on Cloud Foundry (CF). 

![](https://github.com/pivotalsoftware/cf-r-plumber/blob/misc/Screen%20Shot%202019-04-01%20at%203.48.13%20PM.png)

Note the following important nuances:
* The host should be set as "0.0.0.0" in the pr$run function in [startscript.R](https://github.com/pivotalsoftware/cf-r-plumber/blob/master/startscript.R)
* The port is best set by including PORT <- as.numeric( Sys.getenv('PORT') ) and then supplying PORT as the argument in the pr$run function in [startscript.R](https://github.com/pivotalsoftware/cf-r-plumber/blob/master/startscript.R)

To push this app to your CF environment, run the following command after establishing an API endpoint:
```
cf push rplumber -b https://github.com/cloudfoundry/r-buildpack.git
```

An example API is hosted live on a Cloud Foundry environment (rplumber.apps.pcfdemo.net).  To test the API is working try typing the following into a web browser:
```
http://rplumber.apps.pcfdemo.net/echo?msg=DataScienceonPCF!
```

Also try typing the following simple summing function in a terminal window (return sum of 5 and 6):
```
curl --data "a=5&b=6"  rplumber.apps.pcfdemo.net/sum
```
