<p align="center" >
  <img src="https://s3.amazonaws.com/com.fresconews.v2.prod/static/images/wordmark-transparent-git4.png" alt="Fresco" title="Fresco News">
</p>

A guide to reviewing someone's code and having your code reviewed. Employ this process for every new block of code we plan to push out to production.

### When putting out new code
- Start by submitting a pull request with your new changes. Your pull request should detail the purpose of your code at a high level (new feature for assignments, fixed a bug when adding a payment method, etc.) or provide a link to the ticket/story.
- **Link to the pull request in the ticket/story**
- Find someone that's able to commit to your review and await their feedback on the pull request
- Review their comments and make the necessary changes so that you're both in agreement with the code
- Try to respond to every comment.
- Extract some changes and refactoring into future tickets/stories.
- Merge once you feel confident in the code and its impact on the project.
- Deploy to production as usual

### When reviewing someone else's code
- Understand the change/addition to the code before beginning your review
- Look for ways to simplify the code or remove redundancy while still accomplishing the same thing
  - This could be in the form of an abstraction to better support future reusability
- If you notice a lack of a unit tests for a specific feature that really does need one, mention to this to the author
- Point out potential errors in logic or parts of the code that are just too messy to be easily maintained in the future
- **Style**
    - Check that documentation adheres to the style guide i.e. all function headers are documented clearly, ambiguous code is commented with an explanation
    - Look out for general style errors around conditionals, variable names, method naming, quotations, spacing, etc. 
- Offer alternative implementations, but assume the author already considered them. ("What do you think about using a custom validator here?")
