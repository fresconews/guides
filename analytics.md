# General Notes (Read first)

- Event names and attribute are **case sensitive**!
- Always log object ids of atricles, stories, galleries, etc when creating a call to mix panel along with the required key.
- Mixpanel user keys: `fresco_id`, `username`, `email`, `fullname`

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


## Event Key - `Camera session video duration`

#### Description
> The amount of time a user spends in the camera in one session. 
A session begins when the camera is opened and ends when closed.

#### Note

## Event Key - `Camera session photo count`

#### Description
> The number of photos taken in one session. 
A session begins when the camera is opened and ends when closed.

#### Note
Do you want there to be a video count too? 
Thinking of making count property called count .... I made a property count called count
Add a key value property named activity_duration and attach the time in seconds. Event name stays the same.

## Permissions

### Event Key - `Permissions location {enables,disables}`

#### Description
> Location services are enabled or disabled.

### Event Key - `Permissions notification {enables,disables}`

#### Description
> Notifications are enabled or disabled. 

#### Note
http://stackoverflow.com/a/11649654/5970652


### Event Key - `Permissions camera {enables,disables}`


#### Description
> Camera access is disabled.

### Event Key - `Permissions microphone {enables,disables}`

#### Description
> Microphone access is enabled.

### Event Key - `Permissions photos enables`

#### Description
> Access to photo library granted.

## Signup & Login

### Event Key - `Signup radius changes`

#### Description
> User sets area in which they will be notified of new assignments.

### Event Key - `Signup`

#### Attributes
- social_links ([facebook, twitter])

#### Description
> User signs up through the app

### Event Key - `Login`

#### Attributes
- platform (email, facebook, twitter)

#### Description
> User logs in through the app

## Submissions & Upload

### Event Key - `Submission time writing caption`

#### Attributes
- activity_duration

#### Description
> The amount of time it takes for a user to write a caption.

### Event Key - `Submissions`

#### Attributes
- `videos_submitted` (The number of photos submitted.)
- `photos_submitted` (The number  of videos submitted.)

#### Description
> When a user creates a submissions, with number of photos and videos

### Event Key - `Submission failed`

#### Attributes
- `upload_speed_kBps`
- Hashmap of media type -> file size { video : "50MB", photo: "10MB" }

#### Description
> Tracking upload failures to help debug when the app doesn't crash

#### Notes
http://stackoverflow.com/questions/29795817/get-cellid-mcc-mnc-lac-signal-strength-quality-and-network-in-ios-8-3

https://developer.android.com/reference/android/telephony/PhoneStateListener.html

### Event Key - `Upload debug`

#### Attributes
- `debug_message`
- `upload_speed_kBps`

#### Description
> Tracking upload fall offs to help debug when the app doesn't crash

#### Notes
> I log a custom error message (like null pointer, failure to create file size) and the kBps on successful uploads for a frame of reference

### Event Key - `Upload error`

#### Attributes
- `error_message`
- `upload_speed_kBps`

#### Description
> Tracking upload failures to help debug when the app doesn't crash

#### Notes
> I log the error message and I guess we could log the etag and gallery/post as well.

### Event Key - `Upload incomplete`

#### Attributes
- `debug_message`
- `upload_speed_kBps`

#### Description
> Tracking upload fall offs to help debug when the app doesn't crash

#### Notes
> I log a custom error message (like null pointer, failure to create file size) and the kBps on successful uploads for a frame of reference

### Event Key - `Upload closed`

#### Attributes
- `gallery_id`
- `percent_complete`

#### Description
> When a user closes the app after starting their upload
