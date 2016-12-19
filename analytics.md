
# Screens

> Keys for the screens that should be tracked

- Home — `Home` 
   - `{"feed_type":"highlights"|"following"}`
- Gallery Detail — `Gallery Detail`
- Story Detail — `Story Detail`
- Stories — `Stories`
- Assignments -> `Assignments`
- Profile — `Profile`
- Camera — `Camera`
- Submission Screen -> `Submission`
- Settings — `Settings`
- Payment Method — `Payment Method`
- Identity — `Identity`

# Events

## Gallery

### Event Key - `Gallery opened`

#### Description
> User taps the read more anywhere

#### Attributes
- `gallery_id`
- `opened_from` (highlights, detail, stories, profile, push, etc.)
- `user_id` (if opened profile profile)

### Event Key - `Gallery session`

#### Description
> User begins viewing a gallery

#### Attributes
- `author`
- `gallery_id`
- `tags`
- `highlighted_at`
- `activity_duration`
- `scrolled_percent` (should be total percent scrolled *overall*)
- `opened_from` (highlights, stories, profile, search)


### Event Key - `Gallery shared`

#### Description
> User taps “Read More” to view a gallery

#### Attributes
- `gallery_id`
- `shared_from` (highlights, detail, stories, profile, etc.)
- `user_id` (shared from profile)

### Event Key - `Gallery liked `

#### Attributes
- `liked_from` (highlights, detail, story, profile)
- `user_id` (if action from someone's profile)
- `gallery_id`

#### Description
> User likes a gallery

### Event Key - `Gallery reposted `

#### Attributes
- reposted_from (highlights, detail, story, profile, push)
- user_id (if action from someone's profile)
- gallery_id

#### Description
> User reposts a gallery

## Profile

### Event Key - `Profile session`

#### Attributes
- activity_duration
- galleries_scrolled_past (Number of galleries scrolled past)
- user_id (id of the profile's user)

####Description
> The amount of time a user spends browsing Profile in a session, and the number of galleries a user scrolls past in a session. A session begins when opening the Profile tab and ends when the user navigates to another screen.

## Stories

### Event Key - `Stories session`

#### Attributes
- activity_duration (Seconds in stories)
- stories_scrolled_past (Number of stories scrolled past)

#### Description
> The number of stories a user scrolls past in a session and the amount of time a user spends browsing Stories in a session. 
A session begins when opening the Stories tab and ends when the user navigates to another screen.

#### Note
> "Highlights session time" and "Highlights sesh galleries seen" are wrapped into one event. Attach the fields "activity_duration" with the value in seconds and "count"

## Highlights

### Event Key - `Highlights session`

#### Attributes
- activity_duration
- galleries_scrolled_past (Number of galleries scrolled past)

#### Description
> The amount of time a user spends browsing Highlights in a session, and the amount of galleries a user scrolls past in a session.
A session begins when opening the Highlights tab and ends when the user navigates to another screen.

#### Note
> "Highlights session time" and "Highlights sesh galleries seen" are wrapped into one event. Attach the fields "activity_duration" with the value in seconds and "count"


## Articles

### Event Key - `Article opens`

#### Description
> User taps on article underneath Gallery

#### Attributes
- `article_id`
- `article_url`

## Onboarding

### Event Key - `Onboarding`

#### Description
> User begins onboard (first screen in the app, where they see instructions)

### Event Key - `Onboarding reads`

#### Description
> User completes onboard (user enters the normal app / home screen)

### Event Key - `Onboarding immediate quits`

#### Description
> User exits app before completing onboard (user decided they didn’t want to try the app)

#### Note
Mixpanel sends events you track every 60 seconds in a large bundle. Which is the stupidest thing if you're trying to, oh i don't know, detect if the user terminated the app before onboarding. Can't wait 60 seconds and then send when the app is dead.


## Camera

### Event Key - `Camera session`

#### Attributes
- `activity_duration`

#### Description
> The amount of time a user spends in the camera in one session. 
A session begins when the camera is opened and ends when closed.

#### Note
Add a key value property named activity_duration and attach the time in seconds. Event name stays the same.

### Event Key - `Portrait video attempts`

#### Description
> The amount of time a user spends in the camera in one session. 
A session begins when the camera is opened and ends when closed.

#### Note
Add a key value property named activity_duration and attach the time in seconds. Event name stays the same.
