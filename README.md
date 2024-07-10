# Automated news publishing

![GitHub License](https://img.shields.io/github/license/barrychum/push-news-demo) ![Custom Badge](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/barrychum/0bfe84475b631b5ff3b5e520b30ebac6/raw/guardian-news-last-run-badge.json) 

This repository demonstrates a GitHub workflow that fetches content from The Guardian, a popular UK news provider, and pushes it to a Telegram channel. This setup showcases the workflow's ability to poll various services and publish updates.

## Demo
Subscribe to the Telegram channel https://t.me/demo_channel_all to see it in action. You can open the link from any device with Telegram installed.

## Features
- Fetches news content from The Guardian.
- Pushes news updates to a Telegram channel.
- Automates the entire process using GitHub Actions.

## Usage
The workflow triggers at specified intervals to fetch the latest news and post it to the Telegram channel.  Please refers to the .github/workflows/workflow.yml for details.  

A workflow can also be triggered by an external event.  
In the workflow.yml add the following name
```
on:
  repository_dispatch:
    types: [your-trigger-name]
```

On the triggering side, send a HTTP POST request to the github api
```
curl -X POST \
  -H "Accept: application/vnd.github.+json" \
  -H "Authorization: token <YOUR_PERSONAL_ACCESS_TOKEN>" \
  https://api.github.com/repos/<OWNER>/<REPO>/dispatches \
  -d '{"event_type":"<your-trigger-name>"}'
```

Change YOUR_PERSONAL_ACCESS_TOKEN, OWNER, REPO, your-trigger-name accordingly.


## Conclusion

GitHub workflows are primarily utilized for Continuous Integration and Continuous Deployment (CI/CD), providing an efficient way to automate the build, test, and deployment processes. This automation ensures that code changes are consistently integrated and deployed with minimal manual intervention, enhancing both development speed and reliability.

In addition to CI/CD, GitHub workflows offer powerful capabilities for automating various tasks, as demonstrated in this repository. The automated news publishing setup illustrates how GitHub Actions can be leveraged to:

- **Automate Repetitive Tasks**: Fetching and distributing news content automatically ensures timely and consistent updates without the need for manual involvement.
- **Enhance Reliability**: Scheduled workflows perform tasks at regular intervals, reducing the risk of human error and maintaining a steady flow of operations.
- **Integrate Seamlessly**: With the ability to connect to a wide range of APIs and services, GitHub workflows can automate diverse applications, from data polling and notifications to content management.

While CI/CD remains the primary use case, the versatility of GitHub workflows extends to any scenario where automation can streamline processes and improve efficiency.
