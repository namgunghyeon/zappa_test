# Zappa test
[zappa](https://github.com/Miserlou/Zappa)

api gateway + lambda

## preparation
### aws
```
aws configure --profile <env name>
access_key, secret_key, region setting
```

```
export AWS_PROFILE=<env name>
```
### python3
```
virtualenv -p python3 .env
```

```
. .env/bin/activate
```

```
pip3 install -r requirements.txt
```

## deploy
```shell
(.env) $ zappa deploy dev
Calling deploy for stage dev..
Downloading and installing dependencies..
 - sqlite==python36: Using precompiled lambda package
Packaging project as zip.
Uploading zappa-test-dev-1530714334.zip (5.6MiB)..
100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 5.90M/5.90M [00:00<00:00, 9.38MB/s]
Scheduling..
Scheduled zappa-test-dev-zappa-keep-warm-handler.keep_warm_callback with expression rate(4 minutes)!
Uploading zappa-test-dev-template-1530714339.json (1.6KiB)..
100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.64K/1.64K [00:00<00:00, 23.4KB/s]
Waiting for stack zappa-test-dev to create (this can take a bit)..
100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 4/4 [00:12<00:00,  3.09s/res]
Deploying API Gateway..
Deployment complete!: https://url/dev
```

## undeploy
``` shell
$ zappa undeploy dev
Calling undeploy for stage dev..
Are you sure you want to undeploy? [y/n] y
Deleting API Gateway..
Waiting for stack zappa-test-dev to be deleted..
Unscheduling..
Unscheduled zappa-test-dev-zappa-keep-warm-handler.keep_warm_callback.
Deleting Lambda function..
Done!
```