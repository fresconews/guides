#### Purpose

This is a guideline for determining if a new feature is ready to go for testing. Use these steps while you're developing and after you're done developing.

**Important Note: **Don't think the way you normally do, think the way **a user does**. Our goal is to capture as much as we can before handing our features off to other testers. Don't be afraid to break your code!

#### Step-by-Step guide

1. Test your feature at a high level to see if basic functionality is working
    1. Make sure data persists to all the relevant places (local DB, API, etc.)
    2. Make sure layout behaves as expected

2. Does it work in all use cases?
    1. Think of which inputs are possible that could potentially break the feature
    2. Think of which reachability states could affect the feature's functionality
        1. No internet connectivity
        2. Cellular connectivity
        3. WiFi connectivity

    3. Think of the different types of accounts you can be logged in as and how permissions may affect the feature's functionality
        1. Regular user account
        2. Outlet Account
        3. Admin Account

3. Edge Cases (trying to break it)  

    1. Enter inputs that are completely unexpected and don't make any sense
    2. Limits
        1. Inputs that are too long
        2. Rendering text that's too long
        3. Pictures that are too big (resolution and file size)

4. Edge Cases (larger scope)
    1. Logged in / Logged out state should **always** be tested
    2. Testing against both the development and production API if applicable
    3. Does the interaction's state persist to other places in the app? For example -
        1. If I follow someone here, do they show up followed everywhere else?
        2. If my cells are being resized in this activity/scroll view, are they being properly resized everywhere else?

5. Flow
    1. If the feature spans multiple screens, does navigation work as expected?
        1. Can I go back and forth between views as expected?
        2. Does the app handle exceptions where I shouldn't be able to navigate between specific screens after a certain interaction?
        3. Does closing the app leave the app in the expected state?
        4. Handle all combinations of navigation e.g. two steps forward and one step back, two steps back and one step forward

6. UI
    1. Interacting with the UI **much** faster than a normal user would

7. Legacy Devices
    1. Does the feature behave/render correctly on other screen sizes
    2. Is the feature as performant on weaker devices as it is on your main testing device?

8. Error Handoff
    1. Always, always do your best to determine the reality of a bug someone is facing. If you think it's not real, **really **make sure that it's not. Always better safe than sorry.

#### Example

This is an example of answering the above questions in context of the **search** feature in Fresco's Android app.

1. Test your feature at a high level to see if basic functionality is working
    1. Type in a search query and see if results show up in the correct ordering
    2. Does pagination work for galleries?
    3. Do gallery cell interactions work e.g. liking galleries, stores, reposting galleries, stories
    4. Can I "See All" with all of the models that came back

2. Does it work in all use cases?  

    1. Stories, Galleries, Users - Make sure all combinations come back
    2. What if I search again? Do results keep coming back after I enter new search queries?
    3. Reachability
        1. Search without wifi
        2. Search on a poor connection
        3. Search without any internet connection

3. Edge Cases (trying to break it)  

    1. Clicking on the avatar instead of the username
    2. Type in ridiculous search queries that might not provide results
    3. Don't search for anything
    4. Type in a hash ID
    5. Type spaces before and after the search query

4. Edge Cases (larger scope)  

    1. If I follow someone in the search page, and go to their profile?
    2. What I follow someone, and click "See All users"
    3. Trying to search without being logged in
    4. Production vs. Development API
        1. Logged in, on Production. Logged out, on Development. And so forth.

5. Flow
    1. Going into a profile on a user by selecting a gallery, and going back to the search page
    2. If you're in, "See All Users", and follow someone and then go back to the search preview - does the state persist? What happens when you try to follow them?
    3. What happens when closing the app while searching? Force closing and going to background state
    4. Can I access the search page correctly from all areas of the app and navigate back to where I was.

6. UI
    1. Clicking on search items fast
    2. Scrolling fast
    3. Refresh fast
    4. Switch tabs fast: "See All" and back, "See All" and back

7. Legacy Devices  

    1. Start with Step 1 on legacy devices to make sure it works. A few regular action.
    2. If things seem fine, then continue to step 2 and so forth
