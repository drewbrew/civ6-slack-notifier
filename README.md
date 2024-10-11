# Civilization VI Slack Notifier [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Frobbiedhickey%2Fciv6-slack-notifier&env=SLACK_WEBHOOK_URL&envDescription=You%20can%20generate%20a%20Slack%20webhook%20URL%20by%20following%20the%20steps%20at%20this%20link%3A%20https%3A%2F%2Fapi.slack.com%2Fmessaging%2Fwebhooks%23create_a_webhook&project-name=civ6-slack-notifier&repo-name=civ6-slack-notifier)

This project aims to make deploying your own Civilization VI `Play By Cloud` webhook as easy as possible. It currently only supports Slack, Discord may be supported in the future but there is already an [excellent project](https://civ.halfstack.software/) catering to that use case.

## Setup 

### Prequisites

[Create a slack webhook](https://api.slack.com/messaging/webhooks#create_a_webhook)

### Deploy Button Setup (Recommended)

The easiest way to get started is to click the `Deploy with Vercel` button in the header. You will be asked to create a Vercel account, which is free. After going through the wizard, you will be asked to provide the slack webhook url as the `SLACK_WEBHOOK_URL` environment variable. Navigate to the deployment once complete - the landing page will present you with the webhook URL you can use to configure the `Play By Cloud Webhook URL` setting in the game options.

### Manual Setup (Advanced)

* Clone/fork this repo
* Sign up for an account at [Vercel](https://vercel.com/signup)
* Install the vercel-cli: `npm install -g vercel`
* Login to vercel: `vercel login`
* Add an environment variable for your webhook: `vercel env add SLACK_WEBHOOK_URL <url>`
* Deploy the stack: `vercel --prod`
* After the deployment is complete, a URL will be copied to your clipboard. Paste the following into your Play by Cloud Webhook setting in your Civ VI game: `{vercel_deployment_url}/api/webhook`

### Optional Enhancements

If you want to include @ mentions in your turn notifications, you can also add a `USER_MAP_JSON` environment variable. It expects a parseable JSON string with a map of `civ_user`->`slack_user_id`:

```json
{"TEST_USER1":"UMTQRM61L","TEST_USER2":"UMK866NQZ"}
```

You can find a user's `slack_user_id` with the steps in [this article](https://moshfeu.medium.com/how-to-find-my-member-id-in-slack-workspace-d4bba942e38c)

## Prior Art

Brett Andrews' work on his https://civ.halfstack.software/ service and the subsequent blog posts were what sparked the idea for this project. 
