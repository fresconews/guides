
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
