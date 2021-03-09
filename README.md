# ecs-hands-on

AWS CLI

```
aws iam create-service-linked-role --aws-service-name ecs.amazonaws.com
touch ecs-task-definition-for-command.json
aws ecs register-task-definition --generate-cli-skeleton >> ecs-task-definition-for-command.json
```