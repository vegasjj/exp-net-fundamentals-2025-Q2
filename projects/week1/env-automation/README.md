# How to Deploy

## Check Your AWS Account

We need to check that we are signed in to the right AWS account

```sh
aws sts get-caller-identity
```

## Run Deploy Script

We moved to the project directory and make the script executable before run it.

```sh
cd projects/week1/env-automation
chmod u+x ./bin/deploy
./bin/deploy
```
