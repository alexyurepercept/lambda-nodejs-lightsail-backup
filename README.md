# Automatic backups for AWS Lightsail

[![Video Instructions Automatic backups for AWS Lightsail](http://img.youtube.com/vi/vUy-eX20nsA/0.jpg)](http://www.youtube.com/watch?v=vUy-eX20nsA)

- [Video Instructions Automatic backups for AWS Lightsail](http://www.youtube.com/watch?v=vUy-eX20nsA)

This script for the AWS Lambda NodeJS is to automate the backup process for your AWS Lightsail instances easily.

The AWS Lightsail is an excellent hosting service to start with it. The Lightsail backups are a no-brainer to use. They are very powerful and incremental. You pay only for the differences in your files. It means you can create a lot of backups without spending a fortune on them. It keeps your work safe. But sorrowfully you cannot set up automatic backups from the console of the service. Now you can solve this problem easily with the help of this manual.

**Benefits**

- Free of charge!
- Once set up, no need to worry
- Daily, weekly and monthly backups

Follow the instructions here for the setup. It is easy!
We will use the AWS Lambda.

## Deploy

Create config.json in the project folder

```
{
        "<stage>": {
                "backupDays": <backup_days>,
                "backupWeeks": <backup_weeks>,
                "backupMonths": <backup_months>,
                "instanceName": "<instance_name>"
        }
}
```

An example would like following

```
{
        "dev": {
                "backupDays": 7, // keep at least 7 daily backups
                "backupWeeks": 4, // keep at least 4  weekly  backups
                "backupMonths": 3, // keep at least 3  monthly  backups
                "instanceName": "lightsail-instance"  // the name of the lightsail instance
        }
}
```

```
serverless deploy --stage <stage> --region <region> --instance_name <instance_name_to_backup>
```

The script will remove old backups, that are not in the range of dates you set. The Lightsail backups are incremental and they are very economical to use for you.

JFYI: Weekly and monthly backups will be saved on Sundays. You need at least 7 daily backups for weekly and monthly backups work correctly.

Copyright 2011-2017 Amazon.com, Inc. or its affiliates. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except in compliance with the License. A copy of the License is located at

http://aws.amazon.com/apache2.0/

## LICENSE

Copyright 2018 Alexey Vidanov

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
