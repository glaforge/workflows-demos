Click the button below to open Cloud Shell, and follow the instructions to deploy the workflow contained in this directory.

[![Open in Cloud Shell](https://gstatic.com/cloudssh/images/open-btn.svg)](https://ssh.cloud.google.com/cloudshell/editor?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fglaforge%2Fworkflows-demos&cloudshell_git_branch=master&cloudshell_print=instructions.txt&cloudshell_workspace=open-in-cloudshell&cloudshell_tutorial=README.md)

In this tutorial, you will enable the Workflows cloud API, and then use the `gcloud` command to deploy a simple workflow
that will log the traditional hello world message.

For reference, here are the instructions you will have to enter in the shell:
```shell
# Run the following commands:

# Enable the Workflows API
gcloud services enable workflows.googleapis.com

# Deploy the workflow of this repository
gcloud workflows deploy hello-world-workflow \
  --source=hello-world-workflow.yaml \
  --location=europe-west1
```

To deploy the following workflow:
```yaml
- hello:
    call: sys.log
    args:
        text: Hello Workflows World!
```
