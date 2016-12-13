<p align="center" >
  <img src="https://s3.amazonaws.com/com.fresconews.v2.prod/static/images/wordmark-transparent-b.png" alt="Fresco" title="Fresco News">
</p>

### Purpose
> This is a guideline for deploying a new iOS/Android/Web build for testing. Whoever is leading the build upload should follow all these steps so we can get valuable feedback and ensure that we'll be able to fix/address any bugs/feedback we receive.
General Guidelines

### Step-by-step guide
1. Once the current sprint is done and it's time to upload a build to get feedback (most often after sprint review), run through each new part of the build and QA to the extent where you feel comfortable with other people using these new features.
2. Test Notes
  * Write up clear and informative release notes so testers know exactly what to test and look out for. Release notes should go in the app listing and in Trello.
  * Test notes should reflect how many different scenarios the tester should put themselves in e.g. being outside on a cellular connection for uploading, signing up with new account and receiving a purchase, etc.
  * Once test notes are written, go over them with Elmir so we can make sure they cover all edge cases we anticipate a feature may break in.
3. Upload the build with its release notes, and inform our internal team that the build is live and ready for feedback in the respective dev channel on Slack (dev-android, - dev-ios, dev-web)
  * Make sure the feedback form is updated with the latest build info i.e Trello (https://trello.com/b/g8ATjltq/ios-feedback, https://trello.com/b/VzFhRjcn/android-feedback, https://trello.com/b/W8cd3i3P/web-feedback)
  * Provide a link to the form in the channel
  * Make sure new team members understand the feedback process and structure on Trello
4. Ensuring proper testing
  * At least 2 people should test each of the new features that need feedback. We can often find people from other departments in Fresco to help conduct this if there aren't - enough people in our internal testing lists to help out.
  * It's extremely important to get steps to re-reproduce, so communicate the need to take notes on how to re-create the issue as your tester tests the new features
5. By the time the new sprint arrives, you should have converted any bugs that are still present in the build into Jira.
6. Every piece of feedback should be addressed by either converting it into a ticket in Jira or by dismissing it as something that isn't relevant. But make sure to mark it as addressed!
7. Making the decision to deploy
  * Once testing feedback is gathered and addressed, meet with Elmir to strategize how much of the feedback should be addressed initially as a requirement for release.
