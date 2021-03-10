# ecs-hands-on

書籍:https://booth.pm/ja/items/2539342

AWS CLI

```

aws iam create-service-linked-role --aws-service-name ecs.amazonaws.com
touch ecs-task-definition-for-command.json
aws ecs register-task-definition --generate-cli-skeleton >> ecs-task-definition-for-command.json
aws ecs register-task-definition --cli-input-json file://ecs-task-definition-for-command.json

```

```
aws ecs run-task \
--cluster ecs-hands-on \
--task-definition ecs-hands-on-for-command \
--overrides '{"containerOverrides": [{"name":"laravel","command": ["sh","-c","php artisan print:helloworld"]}]}' \
--launch-type FARGATE \
--network-configuration "awsvpcConfiguration={subnets=[subnet-XXXXXXXXXXXX],securityGroups=[sg-XXXXXXXXXXXXXX],assignPublicIp=ENABLED}"
```

```
aws ecs register-task-definition --cli-input-json file://ecs-task-definition-for-web.json
```

```
aws ecs create-service \
--cluster ecs-hands-on \
--service-name ecs-hands-on-laravel \
--task-definition ecs-hands-on-for-web \
--launch-type FARGATE \
--desired-count 1 \
--network-configuration "awsvpcConfiguration={subnets=[subnet-XXXXXXXXXXX],securityGroups=[sg-XXXXXXXXXXXXX],assignPublicIp=ENABLED}"
```