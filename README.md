AEM Packer Code Build
----------
Scripts for managing [AWS Code Build](https://aws.amazon.com/codebuild/) projects which use [Packer AEM](https://github.com/shinesolutions/packer-aem).

The scripts require a build specification similar to [this](https://github.com/ibi456/packer-aem/blob/master/buildspec.yml) specified in the repository. Note the environment variables required for the build phase.

AWS CLI commands have to be run independently

Usage
------
- Creating a build project for a component
  * Run `./create_build_project -c <component> -v <version>`
  * Modify the build template `project_config.json` produced from the previous command if required
  * Run `aws codebuild create-project --cli-input-json file://project_config.json `
  * To let builds occur automatically with code changes add a web hook with the following command `aws codebuild create-webhook --project-name <build-project-name>`

- Run build
  * Refer to [Run a build](https://docs.aws.amazon.com/codebuild/latest/userguide/run-build.html#run-build-cli)

- Update details for a build project
  * Refer to [Change project build](https://docs.aws.amazon.com/codebuild/latest/userguide/change-project.html#change-project-cli)

Notes
-----
- The git clone depth has to be set in the AWS console
