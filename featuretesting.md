<p align="center" >
  <img src="https://s3.amazonaws.com/com.fresconews.v2.prod/static/images/wordmark-transparent-git4.png" alt="Fresco" title="Fresco News">
</p>

### Purpose

This is a guideline for determining if a new feature is ready to go for testing. Use these steps while you're developing and after you're done developing.

**Important Note: **Don't think the way you normally do, think the way **a user does**. Our goal is to capture as much as we can before handing our features off to other testers. Don't be afraid to break your code!

### Step-by-Step guide

1. Test your feature at a high level to see if basic functionality is working
  - Make sure data persists to all the relevant places (local DB, API, etc.)
  - Make sure layout behaves as expected

2. Does it work in all use cases?
  - Think of which inputs are possible that could potentially break the feature
  - Think of which reachability states could affect the feature's functionality    
    - No internet connectivity
    - Cellular connectivity
    - WiFi connectivity
    
  - Think of the different types of accounts you can be logged in as and how permissions may affect the feature's functionality
    - Regular user account
    - Outlet Account
    - Admin Account
    
3. Edge Cases (trying to break it)  
  - Enter inputs that are completely unexpected and don't make any sense
  - Limits
    - Inputs that are too long
    - Rendering text that's too long
    - Pictures that are too big (resolution and file size)

4. Edge Cases (larger scope)
  - Logged in / Logged out state should **always** be tested
  - Testing against both the development and production API if applicable
  - Does the interaction's state persist to other places in the app? For example:
    - If I follow someone here, do they show up followed everywhere else?
    - If my cells are being resized in this activity/scroll view, are they being properly resized everywhere else?

5. Flow
  - If the feature spans multiple screens, does navigation work as expected?
    - Can I go back and forth between views as expected?
    - Does the app handle exceptions where I shouldn't be able to navigate between specific screens after a certain interaction?
    - Does closing the app leave the app in the expected state?
    - Handle all combinations of navigation e.g. two steps forward and one step back, two steps back and one step forward

6. UI
  - Interacting with the UI **much** faster than a normal user would

7. Legacy Devices
  - Does the feature behave/render correctly on other screen sizes
  - Is the feature as performant on weaker devices as it is on your main testing device?

8. Error Handoff
  - Always, always do your best to determine the reality of a bug someone is facing. If you think it's not real, **really **make sure that it's not. Always better safe than sorry.

### Example

This is an example of answering the above questions in context of the **search** feature in Fresco's Android app.

1. Test your feature at a high level to see if basic functionality is working
  - Type in a search query and see if results show up in the correct ordering
  - Does pagination work for galleries?
  - Do gallery cell interactions work e.g. liking galleries, stores, reposting galleries, stories
  - Can I "See All" with all of the models that came back

2. Does it work in all use cases?  
  - Stories, Galleries, Users - Make sure all combinations come back
  - What if I search again? Do results keep coming back after I enter new search queries?
  - Reachability
    - Search without wifi
    - Search on a poor connection
    - Search without any internet connection

3. Edge Cases (trying to break it)  
  - Clicking on the avatar instead of the username
  - Type in ridiculous search queries that might not provide results
  - Don't search for anything
  - Type in a hash ID
  - Type spaces before and after the search query

4. Edge Cases (larger scope)  
  - If I follow someone in the search page, and go to their profile?
  - What I follow someone, and click "See All users"
  - Trying to search without being logged in
  - Production vs. Development API
    - Logged in, on Production. Logged out, on Development. And so forth.

5. Flow
  - Going into a profile on a user by selecting a gallery, and going back to the search page
  - If you're in, "See All Users", and follow someone and then go back to the search preview - does the state persist? What happens when you try to follow them?
  - What happens when closing the app while searching? Force closing and going to background state
  - Can I access the search page correctly from all areas of the app and navigate back to where I was.

6. UI
  - Clicking on search items fast
  - Scrolling fast
  - Refresh fast
  - Switch tabs fast: "See All" and back, "See All" and back

7. Legacy Devices  
  - Start with Step 1 on legacy devices to make sure it works. A few regular action.
  - If things seem fine, then continue to step 2 and so forth
