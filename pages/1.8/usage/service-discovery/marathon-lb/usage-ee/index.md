---
layout: layout.pug
title: Installing and Customizing on DC/OS Enterprise
menuWeight: 10
excerpt:

enterprise: true
---

# Installing Marathon-LB

## About installing Marathon-LB

The installation procedure varies according to your [security mode](/1.8/administration/installing/ent/custom/configuration-parameters/#security). Refer to the section that corresponds to your security mode for step-by-step instructions.

- [`disabled` and `permissive` modes](#mlb-disabled-install)
- [`strict` mode](#mlb-strict-perm-install)

## <a name="mlb-disabled-install"></a>Installing in disabled and permissive modes

### Using the DC/OS CLI 

**Prerequisite:** [DC/OS CLI installed](/1.8/usage/cli/install/) and logged in via `dcos auth login` as a user with the [necessary permissions](/1.8/administration/id-and-access-mgt/ent/permissions/).

If you don't want to change any of the default settings, you can install Marathon-LB with the following command.

```bash
dcos package install marathon-lb
```

To customize Marathon-LB, you can use the following command to determine its options.

```bash
dcos package describe --config marathon-lb
```

Create a new `config.json` file to override any one of the default settings and install Marathon-LB using the following command, where `config.json` contains your custom settings.

```bash
dcos package install --options=config.json marathon-lb
```

### Using the Universe

To install Marathon-LB from the Universe in `disabled`and `permissive` modes, log into the DC/OS web interface as a user with the [necessary permissions](/1.8/administration/id-and-access-mgt/ent/permissions/).

Click **Universe** -> **Packages** to open the **Packages** tab. Locate the Marathon-LB package and click **Install**. To install with the default settings, click **Install Package**. To customize Marathon-LB, click **Advanced Installation**.

## <a name="mlb-strict-perm-install"></a>Installing in strict mode

**Prerequisites:** 

- Marathon-LB requires a service account in `strict` [security mode](/1.8/administration/installing/ent/custom/configuration-parameters/#security). Only someone with the `superuser` permission can create the service account. Refer to [Provisioning Marathon-LB](/1.8/administration/id-and-access-mgt/ent/service-auth/mlb-auth/) for instructions.

- [DC/OS CLI installed](/1.8/usage/cli/install/) and logged in via `dcos auth login` as a user with the [necessary permissions](/1.8/administration/id-and-access-mgt/ent/permissions/).

The parameters shown in [Provisioning Marathon-LB](/1.8/administration/id-and-access-mgt/ent/service-auth/mlb-auth/) are required to install Marathon-LB. You may wish to modify other default values before installing the service. To view the configuration options and defaults of Marathon-LB, type the following command.

```bash
dcos package describe --config marathon-lb
```

Once you have the `config.json` file with the required and optional parameters, use the following command to install.

```bash
dcos package install --options=config.json marathon-lb
```

# Next steps

- [Tutorial - Deploying a Load Balanced App with Marathon-LB](/1.8/usage/service-discovery/marathon-lb/marathon-lb-basic-tutorial/)
- [Tutorial - Using Marathon-LB for Internal and External Load Balancing](/1.8/usage/service-discovery/marathon-lb/marathon-lb-advanced-tutorial/)
- See the advanced Marathon-LB [documentation](/1.8/usage/service-discovery/marathon-lb/advanced/).

 [1]: /1.8/administration/installing/ent/
 [2]: /1.8/usage/cli/install/
 [3]: /1.8/administration/managing-aws/
 [4]: /1.8/administration/access-node/sshcluster/
