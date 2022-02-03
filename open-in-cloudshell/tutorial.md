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
  --location=europe-west1 \
  --project=<walkthrough-project-id/>
```

The workflow will be deployed in the `europe-west1` region,
but you can also pick from:

* `asia-southeast1` (Singapore)
* `europe-west1` (Belgium)
* `europe-west4` (Netherlands)
* `europe-west6` (Zurich)
* `us-central1` (Iowa)
* `us-east1` (South Carolina)

You should see an output similar to the following one:

```
Waiting for operation [operation-1643902570147-5d71ee4bd2d0b-406a7840-b007194b] to complete...done.   
createTime: '2022-02-03T15:36:10.340979362Z'
name: projects/<walkthrough-project-id/>/locations/europe-west1/workflows/hello-world-workflow
revisionCreateTime: '2022-02-03T15:36:10.373188680Z'
revisionId: 000001-061
serviceAccount: projects/<walkthrough-project-id/>/serviceAccounts/783131360595-compute@developer.gserviceaccount.com
sourceContents: |
  - hello:
      call: sys.log
      args:
          text: Hello Workflows World!
state: ACTIVE
updateTime: '2022-02-03T15:36:10.810361998Z'
```

Once deployed successfully, you will create the first execution of the workflow.

## Execute the workflow

Create the first execution of your workflow with the following command:

```bash
gcloud workflows run hello-world-workflow \
  --project=<walkthrough-project-id/>
```

You can use `run` command as above to execute the workflow and wait for the execution to complete,
or the `execute` command to launch the execution without waiting for the execution attempt to finish.

A successful run attempt should give you the following output:

```
Waiting for execution [3e5cc9fe-5685-4b3f-885e-3f03274905df] to complete...done.     
argument: 'null'
endTime: '2022-02-03T15:40:52.966351644Z'
name: projects/783131360595/locations/europe-west1/workflows/hello-world-workflow/executions/3e5cc9fe-5685-4b3f-885e-3f03274905df
result: 'null'
startTime: '2022-02-03T15:40:52.647741619Z'
state: SUCCEEDED
workflowRevisionId: 000001-061
```

## Conclusion

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

Congratulations, you've deployed your first workflow, and created its first execution!

<walkthrough-inline-feedback></walkthrough-inline-feedback>

If you're interested in more examples of Google Cloud Workflows,
please head over to our [Workflows](https://cloud.google.com/workflows) samples, 
and follow the instructions!
