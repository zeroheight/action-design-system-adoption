<p align="center">
  <a href="https://zeroheight.com">
    <img src="https://zeroheight-wordpress-uploads.s3.amazonaws.com/wp-content/themes/zhwebsite/assets/images/logo.svg" width="200px" alt="zeroheight" />
  </a>
</p>

<h2 align="center">Analyze and track design system adoption</h2>

<p align="center">
    This <a href="https://github.com/features/actions">GitHub action</a> allows you to automatically analyze and push design system adoption data directly to zeroheight!
</p>


![Component adoption screen in zeroheight](https://zeroheight-wordpress-uploads.s3.amazonaws.com/wp-content/uploads/2024/06/CleanShot-2024-06-19-at-09.00.19@2x-2048x893.png)

---

**Learn more about zeroheight's design system adoption features, such as [component usage tracking](https://zeroheight.com/help/article/component-usage/) and [package monitoring](https://zeroheight.com/help/article/package-version-monitoring/), in [our learning hub](https://zeroheight.com/help/article/adoption-private-beta-overview/#experimental-features) or check out the linked video below.**

[<img src="https://img.youtube.com/vi/U7Lp2iVIs7k/maxresdefault.jpg" width="100%" alt="YouTube video" />](https://youtu.be/U7Lp2iVIs7k)

---

## Getting started

> [!NOTE]
> This action presumes you already have a zeroheight account. You can [sign up here](https://zeroheight.com/create/account?utm_department=marketing&utm_source=github).

1. Head to [`zeroheight.com/adoption`](https://zeroheight.com/adoption) and follow the steps to connect your design system packages and application source code to zeroheight
3. Use the component tracking setup steps to create a Client ID and Access Token and ensure to note these down for future use
4. Now head over to your application's source code on GitHub and enter your zeroheight Client ID and Access Token as GitHub repository secrets (Settings → Secrets and variables → Actions) using `ZEROHEIGHT_CLIENT_ID` and `ZEROHEIGHT_ACCESS_TOKEN` respectively
5. Once complete, add the following step to your existing GitHub Action workflow file:
   ```yaml
      - name: Analyze design system adoption data
        uses: zh-ski/action-design-system-adoption@v1
        env:
          ZEROHEIGHT_CLIENT_ID: "${{ secrets.ZEROHEIGHT_CLIENT_ID }}"
          ZEROHEIGHT_ACCESS_TOKEN: "${{ secrets.ZEROHEIGHT_ACCESS_TOKEN }}"
   ```
   We recommend adding it as part of your post-deployment workflows. If you're new to workflows and actions check out [GitHub's Actions documentation](https://docs.github.com/en/actions) for more info.
6. Save your changes, trigger your action, and check in zeroheight to see design system usage data come in 🎉

**Check out [our example React application](https://github.com/zeroheight-demos/example-airorange-app) for reference and [it's containing GitHub Action file](https://github.com/zeroheight-demos/example-airorange-app/blob/master/.github/workflows/deploy.yaml).**
