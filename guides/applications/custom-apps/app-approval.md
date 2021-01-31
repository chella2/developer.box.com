---
rank: 4
related_endpoints: []
related_guides: []
required_guides:
  - applications/custom-apps/app-token-setup
  - applications/custom-apps/jwt-setup
related_resources: []
alias_paths: []
category_id: applications
subcategory_id: applications/custom-apps
is_index: false
id: applications/custom-apps/app-approval
type: guide
total_steps: 4
sibling_id: applications/custom-apps
parent_id: applications/custom-apps
next_page_id: ''
previous_page_id: applications/custom-apps/app-token-setup
source_url: >-
  https://github.com/box/developer.box.com/blob/main/content/guides/applications/custom-apps/app-approval.md
fullyTranslated: true
---
# アプリの承認

Application that are configured with [JWT][jwt], [Client Credentials Grant][ca], or [App Token][app-token] authentication must be authorized by a Box enterprise Admin before it can be used.

## 承認の通知

A semi-automated process for app approval is available in the Developer Console.

Navigate to the **Authorization** tab for your application in the [Developer console][devconsole].

<ImageFrame border width="400" center>

![キーの追加と管理](../images/app-authorization.png)

</ImageFrame>

Submitting the application for approval will send an email to your enterprise's Admin to approve the application. More information on this process is available in our [support article on app authorization][app-auth].

## 手動による承認

If the above process is not an option, the following steps provide instructions on how to manually approve the application.

### 開発者の場合

As the developer, navigate to the **Configuration** tab for your application in the [Developer Console][devconsole]. Scroll down to the OAuth 2.0 Credentials section and copy the Client ID value to provide to your Box Admin.

<Message>

# Box管理者の確認方法

If you don't know your enterprise Admin, go to your Box [Account Settings][settings] page and scroll to the bottom. If an admin contact is set you should see their contact information under "Admin Contact".

</Message>

### As Admin

As a Box Admin, navigate to the [Admin Console][adminconsole] and select the **Apps** tab (1) from the left navigation panel. Then, click the **Custom Apps** tab (2) at the top of your screen. On this screen, you will see a **+** button in the top right corner to add a new app authorization.

<ImageFrame border center>

![\[アプリ\]タブ](../images/apps.png)

</ImageFrame>

In the popup that appears, enter the client ID for the application that the developer collected from the **Configuration** tab of the Developer Console.

## 変更の再承認

アプリケーションのスコープまたはアクセスレベルが変更された場合は、アプリケーションを再承認する必要があります。新しい変更を有効にするには、上記のプロセスを繰り返して新しいアクセストークンをリクエストしてください。

In the same section where the application was initially authorized, an Admin can re-authorize the application by clicking on the ellipses to the right of the application name and selecting "Reauthorize App".

<ImageFrame border center>

![アプリの再承認](../images/app-reauthorize.png)

</ImageFrame>

[devconsole]: https://app.box.com/developers/console

[ca]: g://authentication/jwt/without-sdk/#client-credentials-grant

[settings]: https://app.box.com/account

[adminconsole]: https://app.box.com/master/settings/custom

[jwt]: g://authentication/jwt

[app-token]: g://authentication/app-token

[app-auth]: https://community.box.com/t5/Managing-Developer-Sandboxes/Authorizing-Apps-in-the-Box-App-Approval-Process/ta-p/77293
