<p align="center">
  <a href="https://zeroheight.com">
    <img src="https://zeroheight-wordpress-uploads.s3.amazonaws.com/wp-content/themes/zhwebsite/assets/images/logo.svg" width="100px" alt="zeroheight" />
  </a>
</p>

<h2 align="center">Analyze and track design system adoption</h2>

<p align="center">
    This <a href="https://github.com/features/actions">GitHub action</a> allows you to automatically analyze and push design system adoption data directly to zeroheight!
</p>

![Adoption screen in zeroheight](https://zeroheight-wordpress-uploads.s3.amazonaws.com/wp-content/uploads/2025/03/Screenshot-2025-03-25-at-8.23.05%E2%80%AFam.png)

---

**Learn more about zeroheight's design system adoption features, such as [component usage tracking](https://zeroheight.com/help/article/component-usage/), [color usage](https://zeroheight.com/help/article/measure-color-usage/), and [package monitoring](https://zeroheight.com/help/article/package-version-monitoring/), in [our learning hub](https://zeroheight.com/help/article/adoption-private-beta-overview/#experimental-features) or check out the linked video below.**

<p align="center">
[<img src="https://img.youtube.com/vi/U7Lp2iVIs7k/maxresdefault.jpg" width="50%" alt="YouTube video"/>](https://youtu.be/1Sx2ChrFlZw)
</p>

---

## Getting started

> [!NOTE]
> This action presumes you already have a zeroheight account. You can [sign up here](https://zeroheight.com/create/account?utm_department=marketing&utm_source=github).

1. Head to [`zeroheight.com/adoption`](https://zeroheight.com/adoption) and follow the steps to connect your design system packages and application source code to zeroheight
2. Follow the "Use the CLI" flow to create a Client ID and Access Token and ensure to note these down for future use
3. Now head over to your application's source code on GitHub and enter your zeroheight Client ID and Access Token as GitHub repository secrets (Settings → Secrets and variables → Actions) using `ZEROHEIGHT_CLIENT_ID` and `ZEROHEIGHT_ACCESS_TOKEN` respectively
4. Once completed you can use the action as part of your GitHub Action workflow file
5. Once your workflow is updated, trigger your action, and check in zeroheight to see design system usage data come in 🎉

## Usage

### Analyzing component and color usage

```yaml
- name: Analyze design system adoption data
  uses: zeroheight/action-design-system-adoption@v2
  with:
    command: "analyze"
    arguments: '--ignore "**/*.spec.*" --repo-name "my repo"'
  env:
    ZEROHEIGHT_CLIENT_ID: "${{ secrets.ZEROHEIGHT_CLIENT_ID }}"
    ZEROHEIGHT_ACCESS_TOKEN: "${{ secrets.ZEROHEIGHT_ACCESS_TOKEN }}"
```

### Tracking version of design system package

```yaml
- name: Track package version
  uses: zeroheight/action-design-system-adoption@v2
  with:
    command: "track-package"
  env:
    ZEROHEIGHT_CLIENT_ID: "${{ secrets.ZEROHEIGHT_CLIENT_ID }}"
    ZEROHEIGHT_ACCESS_TOKEN: "${{ secrets.ZEROHEIGHT_ACCESS_TOKEN }}"
```

### Monitor package versions being used

```yaml
- name: Track package version
  uses: zeroheight/action-design-system-adoption@v2
  with:
    command: "monitor-repo"
  env:
    ZEROHEIGHT_CLIENT_ID: "${{ secrets.ZEROHEIGHT_CLIENT_ID }}"
    ZEROHEIGHT_ACCESS_TOKEN: "${{ secrets.ZEROHEIGHT_ACCESS_TOKEN }}"
```

We recommend adding it as part of your post-deployment workflows. If you're new to workflows and actions check out [GitHub's Actions documentation](https://docs.github.com/en/actions) for more info.

### Inputs

- `command` - The CLI command to run, can be one of `analyze`, `track-package` or `monitor-repo`
- `arguments` - Optionally provide additional arguments to pass to the command

### Environment Variables

- `ZEROHEIGHT_CLIENT_ID` - Client ID for the authentication token generated in zeroheight
- `ZEROHEIGHT_ACCESS_TOKEN` - Access Token for the authentication token generated in zeroheight

See the [CLI documentation](https://www.npmjs.com/package/@zeroheight/adoption-cli) for more details on the commands and arguments

## Example

**Check out [our example React application](https://github.com/zeroheight-demos/example-airorange-app) for reference and [it's containing GitHub Action file](https://github.com/zeroheight-demos/example-airorange-app/blob/master/.github/workflows/deploy.yaml).**
