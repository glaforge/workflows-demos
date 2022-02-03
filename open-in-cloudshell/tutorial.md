# Deploy your first workflow

## Introduction

In this walkthrough, you'll learn how to deploy your first workflow, and execute it.

<walkthrough-tutorial-duration duration="5"></walkthrough-tutorial-duration>

## Project setup

GCP organizes resources into projects. This allows you to
collect all of the related resources for a single application in one place.

Begin by creating a new project or selecting an existing project for this
tutorial.

<walkthrough-project-setup billing></walkthrough-project-setup>

For details, see
[Creating a project](https://cloud.google.com/resource-manager/docs/creating-managing-projects#creating_a_project).

If you are using `gcloud` in the shell, select your project as follows:

```bash
gcloud config set project [YOUR-PROJECT-ID]
```

## Enable the Workflows API

To be able to use Workflows in your project, you must enable the Workflows API.

<walkthrough-enable-apis apis="workflows.googleapis.com"></walkthrough-enable-apis>

When using the `gcloud` command-line tool, you would run the following command to enable Workflows:

```sh
gcloud services enable workflows.googleapis.com --project=<walkthrough-project-id/>
```

## Your first workflow

Let's start by looking at the 
<walkthrough-editor-open-file filePath="hello-world-workflow.yaml">
definition
</walkthrough-editor-open-file>
of your first workflow.

The workflow consists in a single step, that logs a message in Cloud Logging:

```yaml
- hello:
    call: sys.log
    args:
        text: Hello Workflows World!
```

## Deploy the workflow

To deploy the workflow, execute the following command in the shell:

```bash
gcloud workflows deploy hello-world-workflow \
  --source=hello-world-workflow.yaml \
  --location=europe-west1
```

The workflow will be deployed in the `europe-west1` region,
but you can also pick from:

* `asia-southeast1` (Singapore)
* `europe-west1` (Belgium)
* `europe-west4` (Netherlands)
* `europe-west6` (Zurich)
* `us-central1` (Iowa)
* `us-east1` (South Carolina)

Once deployed successfully, you will create the first execution of the workflow.

## Execute the workflow

Create the first execution of your workflow with the following command:

```bash
gcloud workflows run hello-world-workflow
```

You can use `run` command as above to execute the workflow and wait for the execution to complete,
or the `execute` command to launch the execution without waiting for the execution attempt to finish.

## Conclusion

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

Congratulations, you've deployed your first workflow, and created its first execution!

<walkthrough-inline-feedback></walkthrough-inline-feedback>

If you're interested in more examples of Google Cloud Workflows,
please head over to our [Workflows](https://cloud.google.com/workflows) samples, 
and follow the instructions!
