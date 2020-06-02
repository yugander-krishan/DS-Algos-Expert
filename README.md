# DS-Algos-Expert

LPT Template Package
==

This package contains a Live Pipeline Templates (LPT) template used to define your software infrastructure, including your pipeline, environments, and monitoring. Please follow our [step by step guide](https://w.amazon.com/index.php/LivePipelineTemplates/UserGuide/SynthesisGettingStartedStepByStep) for a complete quickstart guide to creating your infrastructure. The template class itself (presto_linux_code_deploy_lpt.rb in this package) contains links to more documentation.

## How do I start using this package?
You should bring this package into its own workspace to run LPT's tasks and create resources declared with this template:

```
brazil ws --create --name PrestoLinuxCodeDeployLpt --versionSet LivePipelineTemplates/release
cd PrestoLinuxCodeDeployLpt
brazil ws --use --package PrestoLinuxCodeDeployLpt
cd src/PrestoLinuxCodeDeployLpt
```

## What version set and workspace should I use with this package?
You should use `PrestoSpiderPorkServer/lpt`

Your workspace's version set can be changed with:

```
brazil ws --use --versionSet PrestoSpiderPorkServer/lpt
```

## How do I create my template's resources?
Once you have a workspace set up with this package, you should first visualize your pipeline as its used for testing before updating the actual pipeline. Read more about it [here](https://w.amazon.com/bin/view/LPTVisualize)

```
PRESTO_PIPELINE_TYPE=<PIPELINE_NAME> brazil-build visualize
```
where **PIPELINE_NAME** is `presto-code-deploy` OR `presto-mainline`

Once you have tested the pipeline using visualize you can start updating the actual pipeline by synthesizing your resources using LPT's tasks:

```
PRESTO_PIPELINE_TYPE=<PIPELINE_NAME> brazil-build synthesize
```
where **PIPELINE_NAME** is `presto-code-deploy` OR `presto-mainline`

This will begin an interactive prompt requiring confirmation of resource creation.

## How do I synthesize just my pipeline?
You can synthesize pipeline changes only with the `synthesize-pipeline` task:

```
brazil-build synthesize-pipeline
```

## How do I create my monitors and alarms?
To dryrun/preview your monitors and alarms:

```
brazil-build dryrun-alarms
```

To create/update your monitors and alarms:

```
brazil-build activate-alarms
```

## How do I test my template?
Some test examples are included in this package's `spec/` directory. They are run as part of a regular `release` build:

```
brazil-build release
```
