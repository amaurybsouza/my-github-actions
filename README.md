# Awesome GitHub Actions

I have create this repository to keep all the actions developed by me in one place, that's here. Feel free to colaborating with me on this according to the #contribute session. Is a way to leverage the professionals and me to stay always up-to-date and in match with the newest solutions around GitHub Actions.

## What's GitHub Actions?
[GitHub Actions](https://docs.github.com/pt) is a continuous integration and continuous delivery (CI/CD) platform that lets you automate your build, test, and deployment pipeline. GitHub Actions goes beyond just DevOps and lets you run workflows when other events happen in your repository. For example, you can run a workflow to automatically add the appropriate labels whenever someone creates a new issue in your repository.

## Main Components
- **workflows:** an configurable automated process that runs one or more jobs.
- **events:** an event is a specific activity in a repository that triggers a workflow run.
- **jobs:** a job is a set of steps in a workflow that execute on the same runner
- **actions:** an action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task. 
- **runners:** an executor is a server that runs your workflows when they are triggered.

## Basic Example
GitHub Actions uses YAML syntax to define the workflow. Each workflow is stored as a separate YAML file in your code repository, in a directory named `.github/workflows`. You can create an example workflow in your repository that automatically triggers a series of commands whenever code is pushed

1- In your repository, create the `.github/workflows/` directory to store your workflow files.

2- In the `.github/workflows/` directory, create a new file called `learn-github-actions.yml` and add the following code.

```yml
name: learn-github-actions
run-name: ${{ github.actor }} is learning GitHub Actions
on: [push]
jobs:
  check-bats-version:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '14'
      - run: npm install -g bats
      - run: bats -v
```

## How GH Actions authenticate on Azure
In this example, you will create a secret named AZURE_CREDENTIALS that you can use to authenticate with Azure.

1- Use the Azure CLI locally to run some commands.
2- Create a new service principal in the Azure portal for your app. The service principal must be assigned the Contributor role.

```bash
az ad sp create-for-rbac --name "myApp" --role contributor \
                                --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group} \
                                --sdk-auth
```

3- Copy the JSON object for your service principal.

```bash
{
    "clientId": "<GUID>",
    "clientSecret": "<GUID>",
    "subscriptionId": "<GUID>",
    "tenantId": "<GUID>",
    (...)
}
```
4- Open your GitHub repository and go to `Settings` and configure the `Secrets` under `Action` with JSON information.

## Community Articles
I have check some contents about the GitHub Actions around IT community and some of them interesting me.

- [Github Actions: uma introdução](https://www.zup.com.br/blog/github-actions-ci-cd)
- [10 boas práticas e dicas para usar o GitHub Actions](https://www.zup.com.br/blog/github-actions-dicas-boas-praticas)
- [Useful Actions](https://github.com/GuillaumeFalourd/useful-actions)

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)