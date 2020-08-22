#### Postman

-------------------------------------------------------------------------------------------

> Ref url:
> https://www.getpostman.com/docs/



----------------------------------------------



**Command line to execute collection:**

> **reference-guide::**
> https://learning.postman.com/docs/running-collections/using-ne wman-cli/command-line-integration-with-newman/
> https://medium.com/velotio-perspectives/api-testing-using-postman-and-newman-6c68c33303fc
> https://www.npmjs.com/package/newman

**Pre Requirements:**

1. node
2. npm
3. newman packgae (npm install -g newman)

Export the collection we want to execute

**cmd to execute collection**

```
$ newman run <collection>.json 
```

**cmd to execute collection with environment**

```
$ newman run <collection>.json  -e stage.postman_environment.json
```

**Reporters with Newman**
Reports provide the info about the collection which we run

We can use  -r or --reporters options to generate reporters

> Newman inbuilt reoprters: cli, json, junit. 

Command to generate cli & json reporters:

```
$ newman run <collection>.json -r cli,json
```

