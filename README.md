# aws-node

### create basic node project

to create node project    
```bash
$ npm init --yes
```

to create .gitignore  for node
```bash  
$ npx gitignore node   
```

to check is gitignore file created    
```bash
$ ls -a
```

install use packages    
```javascript
$ npm i express mongodb --save
```
to check package.json file.
```bash
$ less package.json    
```

create basic node.js application         
```javascript
const express = require('express');
const app = express();


app.get('/', (req, res)=>{
    res.send("welcome to the home page");
})

// PORT should be in capital letters
const port = process.env.PORT || 3000 ; // aws required this custom port
app.listen( port , ()=>{
    console.log('app start to work at port', port);
});
```

### create aws account   


###  aws config

1. got to "AWS Management Console".
2. select "Elastic Beanstalk" from services.    
3.    

### create code pipe line    
this is for auto update your application when did some changes on repository(github).

1. select "codepipeline" service.    
2. click the "create pipeline" button.     
3. fill the form and click next.    
4. select from which source aws listen changes.(select github version1)
       here you have several options. github,. ..
5. "Add build stage"  skip ****     
6. Add deploy stage
   6.1 Deploy provider select as "AWS Elastic Beanstalk".     
   6.2 set "Application name" as "Elastic Beanstalk" name.      
   6.3 select "Platform" as "Node.js"     .
          app name : created app name with "elastic beanstalk"
          env name : you can get env name from  "Elastic Beanstalk > Environments"
7. wait until "Elastic Beanstalk" created if you create it this stage.
     see here "Elastic Beanstalk > Environments > Nodetest-env"
8. top of the  "Elastic Beanstalk" you can see the link to the server.
9. sometime you need to change port using "Nodetest-env".     
    Nodetest-env > Configuration > [select] "software" edit > set "port" to "8081"    

### add domain to your application

1. search "Route 53" on service bar and select "Route 53" and go to the "Hosted zones".    
2. Route 53 > Hosted zones > Create hosted zone.
   Fill the domain name and click "Create hosted zone".
3. to create record for created host zone.
   Route 53 > Hosted zones > <your domain name>
   1. add "Record name" eg: www    
   2. selectt "Record type" eg: A- Routes traffic to an IPv4 ..   
   3. select "Route traffic to" eg: Alias to Elastic Beanstalk ... and region
   4. add your environment name that create in Elastic Beanstalk eg:"Nodetest-env"  
   5. select "Routing policy" eg: Simple routing    
   6. and click "Create records"    
