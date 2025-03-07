---
title: Getting the most out of your included usage
shortTitle: Included usage
allowTitleToDifferFromFilename: true
intro: 'Find out about the free use of {% data variables.product.prodname_github_codespaces %} that''s included with personal accounts.'
versions:
  fpt: '*'
  ghec: '*'
type: reference
topics:
  - Codespaces
---

Personal {% data variables.product.prodname_dotcom %} accounts include a quota of free use of {% data variables.product.prodname_github_codespaces %} every month.

{% note %}

**Note**: Free use of {% data variables.product.prodname_github_codespaces %} is included in personal accounts only. It is not included in organization or enterprise accounts.

{% endnote %}

There are two types of {% data variables.product.prodname_codespaces %} usage: compute and storage. During your monthly billing period, as you use {% data variables.product.prodname_codespaces %}, your compute and storage usage is deducted from the quota of free usage that's included in your personal {% data variables.product.prodname_dotcom %} account, until either compute or storage is consumed. Once one of those limits is reached, you will not be able to create new codespaces or open existing codespaces until your quota renews, unless you've set up a spending limit and a payment method.

The amount of free usage provided on your personal account every month is designed to allow you to make open source contributions, or to work on side projects, free of charge. It is not intended to be enough for you to do everyday work free of charge.

## About {% data variables.product.prodname_codespaces %} compute

{% data variables.product.prodname_codespaces %} compute is counted in core hours, which is the sum of the time a codespace is active, multiplied by the multiplier for the codespace's machine type: for example, a multiplier of 2 for a 2-core machine, or a multiplier of 8 for an 8-core machine. A codespace becomes active when you create it or start it. A codespace stops being active when you stop it or delete it, or when it is stopped or deleted automatically.

The default idle timeout, which stops a codespace after a period of inactivity, is 30 minutes. You can reduce this if required. For more information, see the "Billing for compute usage" section of "[About billing for {% data variables.product.prodname_github_codespaces %}](/billing/managing-billing-for-github-codespaces/about-billing-for-github-codespaces#billing-for-compute-usage)."

## About {% data variables.product.prodname_codespaces %} storage

You can see the storage usage for each of your codespaces on the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).

![Screenshot of codespaces listed on the 'Your codespaces' page](/assets/images/help/codespaces/click-name-codespace.png)

{% note %}

**Notes**
- If the dev container for a codespace was built from the default image, the size of the codespace shown on this page does not include the size of the base dev container. Storage for the base dev container is provided free of charge. For more information, see "[Storage usage for your base dev container](#storage-usage-for-your-base-dev-container)" below.
- The "Your codespaces" page does not list any prebuilds you may have set up. Prebuilds consume storage for a repository, even if you do not currently have any codespaces for that repository. For more information, see "[About {% data variables.product.prodname_github_codespaces %} prebuilds](/codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds)."

{% endnote %}

For billing purposes, {% data variables.product.prodname_codespaces %} storage is counted in GB-months. This is a cumulative measure of the total storage each codespace consumes from creation to deletion, plus the storage for prebuilds. For more information, see the "Billing for storage usage" section of "[About billing for {% data variables.product.prodname_github_codespaces %}](/billing/managing-billing-for-github-codespaces/about-billing-for-github-codespaces#billing-for-storage-usage)."

## Understanding your {% data variables.product.prodname_codespaces %} usage

You can check the cumulative {% data variables.product.prodname_github_codespaces %} usage for your current monthly billing cycle in your {% data variables.product.prodname_dotcom %} settings. For more information, see "[Viewing your {% data variables.product.prodname_github_codespaces %} usage](http://127.0.0.1:4000/en/billing/managing-billing-for-github-codespaces/viewing-your-github-codespaces-usage)."

![Screenshot of the initial view of personal usage](/assets/images/help/codespaces/view-personal-usage-collapsed.png)

For more specific information - for example, if you want to know which repositories have prebuilds that are consuming storage - you can generate a usage report. The usage report is a CSV file that's emailed to you. For more information on how to generate a usage report, see "[Viewing your {% data variables.product.prodname_github_codespaces %} usage](/billing/managing-billing-for-github-codespaces/viewing-your-github-codespaces-usage)."

To see your {% data variables.product.prodname_codespaces %} usage, filter the report to show only rows that mention "Codespaces" in the `Product` column.

![A screenshot of a usage report in Microsoft Excel](/assets/images/help/codespaces/usage-report-personal-account.png)

### Storage usage for your base dev container

If you don't add a dev container configuration to your repository, or if your configuration does not specify an image to use, then {% data variables.product.prodname_dotcom %} creates a container from a default Linux image. Storage of base dev containers built from the default Linux image is free of charge and does not consume your included storage. Your storage usage will be based only on the files in your repository, and any files you subsequently add to the codespace, including {% data variables.product.prodname_vscode_shortname %} extensions. If you use an alternative base image, then the resulting container and all of the files in the codespace will be counted as used storage. {% data reusables.codespaces.default-image-contents %}

You can check which image was used to create a codespace's dev container. In the Terminal of your codespace, run this command.

```shell{:copy}
devcontainer-info
```

If the dev container for the current codespace was built from the default image, the output of this command will contain the following information.

```
- Definition ID: universal
- Source code repository: https://github.com/devcontainers/images
```

## Tips for making your allowed usage go further

- Your codespaces consume compute usage while they are running. If you're not using a codespace, stopping the codespace prevents unnecessary compute usage. For more information, see "[Stopping and starting a codespace](/codespaces/developing-in-codespaces/stopping-and-starting-a-codespace)."
- You can reduce the idle timeout for {% data variables.product.prodname_codespaces %} in your personal settings to less than the default 30 minutes. This will shorten the period of inactivity before your codespaces are automatically stopped. This can save on compute usage. For more information, see "[Setting your timeout period for {% data variables.product.prodname_github_codespaces %}](/codespaces/customizing-your-codespace/setting-your-timeout-period-for-github-codespaces)."
- Your codespaces consume storage while they exist. You should delete a codespace you have finished using and know that you will not use again. For more information, see "[Deleting a codespace](/codespaces/developing-in-codespaces/deleting-a-codespace)."
- Configure your retention period to ensure codespaces you forget to delete are deleted automatically. The default retention period is 30 days. For more information, see "[Configuring automatic deletion of your codespaces](/codespaces/customizing-your-codespace/configuring-automatic-deletion-of-your-codespaces)."
- {% data variables.product.prodname_vscode %} extensions consume storage. Make sure you are only installing extensions that you need. You can find out how much space is being used by extensions by running this command in your codespace.
  ```shell{:copy}
  du -h -s ~/.vscode-remote/extensions
  ```
- Monitor your compute and storage usage by going to your billing page on {% data variables.product.prodname_dotcom_the_website %}, https://github.com/settings/billing, and reviewing the figures in the "{% data variables.product.prodname_codespaces %}" section.
  {% note %}

  **Note**: Storage is calculated hourly and added to your existing storage usage. Consumed storage is therefore cumulative for the duration of your month-long billing cycle. This means that, during the billing period, the value you see on your billing page will only increase or remain the same. Usage will be reset to zero when a new billing cycle starts. Deleting a codespace, or a prebuild, will not reduce the usage figure for the current month, but it will reduce the rate at which storage usage accumulates.

  {% endnote %}
- Ensure that you are using prebuilds for only as many versions and as many regions as you need. For more information, see "[About GitHub Codespaces prebuilds](/codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds)" and "[About billing for GitHub Codespaces](/billing/managing-billing-for-github-codespaces/about-billing-for-github-codespaces#billing-for-codespaces-prebuilds)."
  {% note %}

  **Note**: If your included storage usage is exhausted, new prebuilds are disabled until you set up a spending limit or your included usage quota renews.

  {% endnote %}
- If you have configured prebuilds in a repository's settings, but you're not using {% data variables.product.prodname_github_codespaces %} for that repository, consider deleting the prebuild configuration to avoid prebuilds for that repository consuming your included storage allowance unnecessarily.

  You can check for prebuild configurations in the "{% data variables.product.prodname_codespaces %}" page of a repository's settings. For more information, see "[Configuring prebuilds](/codespaces/prebuilding-your-codespaces/configuring-prebuilds#configuring-prebuilds)."

  Alternatively, you can check which repositories have prebuilds by reviewing a usage report. For more information, see "[Understanding your {% data variables.product.prodname_codespaces %} usage](#understanding-your-codespaces-usage)" above.
- Storage of containers built from the default Linux image for codespaces is free of charge and does not reduce your included storage. You can therefore avoid your storage allowance being consumed by your dev container by using the default image in your dev container configuration, rather than specifying a more specialized image. For more information, see "[Introduction to dev containers](/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers#using-the-default-dev-container-configuration)" and "[Storage usage for your base dev container](#storage-usage-for-your-base-dev-container)" above.
