# CI-CD-Demo
<!-- TOC -->

- [CI-CD-Demo](#ci-cd-demo)
    - [Overview](#overview)
    - [Contacts](#contacts)
    - [Run Scripts Manually](#run-scripts-manually)
        - [Update Sources](#update-sources)
        - [Update Sources With cleanup/removal](#update-sources-with-cleanupremoval)
    - [Package Only and Inspect output (to QA)](#package-only-and-inspect-output-to-qa)
        - [Build And Deploy to QA](#build-and-deploy-to-qa)
    - [Links](#links)

<!-- /TOC -->

## Overview

This project contains IICS Assets Management Demo

![IICS SDLC](https://lucid.app/publicSegments/view/d3840491-8db9-4ba9-a146-79ea3bb9eb95/image.png)

See CI/CD COnfiguration Examples for different platforms

| Git Hosting  | Pipeline Configuration                             | Description                    |
| ------------ | -------------------------------------------------- | ------------------------------ |
| Bitbucket    | [bitbucket-pipelines.yml](bitbucket-pipelines.yml) | Example pipeline for Bitbucket |
| Github       | [.github](.github)                                 | Example Github Pieplines       |
| GitLab       | [.gitlab-ci.yml](.gitlab-ci.yml)                   | Example Gitlab Pipeline        |
| Azure DevOps | [.ado](.ado)                                       | Example Azure DevOps Pipelines |

## Project Staus Badges

[![Manual Dev Snapshot](https://github.com/jbrazda/CI-CD-Demo/actions/workflows/iics_dev_snapshot.yml/badge.svg)](https://github.com/jbrazda/CI-CD-Demo/actions/workflows/iics_dev_snapshot.yml)
[![Manual Deployment DEV](https://github.com/jbrazda/CI-CD-Demo/actions/workflows/iics_build_deploy_manual.yml/badge.svg?branch=dev)](https://github.com/jbrazda/CI-CD-Demo/actions/workflows/iics_build_deploy_manual.yml)


## Contacts

| Name | Role | Email |
| ---- | ---- | ----- |
|      |      |       |

## Run Scripts Manually

### Update Sources

```shell
ant update.src \
-Diics.release=./conf/iics.release.properties \
-Diics.source.environment=dev
-Diics.export.list.location=./conf/export_list.txt
```

### Update Sources With cleanup/removal

```shell
rm -rf src/iics
ant clean.release -Diics.release=./conf/iics.release.properties
ant update.src \
-Diics.release=./conf/iics.release.properties \
-Diics.source.environment=dev
```

## Package Only and Inspect output (to QA)

```shell
 ant package.src \
 -Diics.release=./conf/iics.release.properties \
 -Diics.target.environment=test \
 -Diics.target.package.config=./conf/all_exclude_connections.package.txt \
 -Diics.package.transform.config=../../../conf/template.transform.properties
```

### Build And Deploy to QA

```shell
 ant build.deploy \
 -Diics.release=./conf/iics.release.properties \
 -Diics.target.environment=test \
 -Diics.target.package.config=./conf/all_exclude_connections.package.txt \
 -Diics.package.transform.config=../../../conf/template.transform.properties \
 -Diics.target.publish.config=./conf/all_designs.publish.txt \
 -Dtools.reporting.disabled=true
```

## Links

- [Automation to Build and Deploy IICS Design Packages](https://github.com/jbrazda/icai-ips-bundle/blob/master/doc/build.md)
- [Github Template Project](https://github.com/jbrazda/iics-project-template)
- [Install IICS Reporting Tool](https://github.com/jbrazda/iics-reporting-tools)
