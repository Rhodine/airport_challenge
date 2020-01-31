Airport Challenge
=================

```
        ______
        _\____\___
=  = ==(____MA____)
          \_____\___________________,-~~~~~~~`-.._
          /     o o o o o o o o o o o o o o o o  |\_
          `~-.__       __..----..__                  )
                `---~~\___________/------------`````
                =  ===(_________)

```

Instructions
---------

* Challenge time: rest of the day and weekend, until Monday 9am
* Feel free to use google, your notes, books, etc. but work on your own
* If you refer to the solution of another coach or student, please put a link to that in your README
* If you have a partial solution, **still check in a partial solution**
* You must submit a pull request to this repo with your code by 9am Monday morning

Steps
-------

1. Fork this repo, and clone to your local machine
2. Run the command `gem install bundle` (if you don't have bundle already)
3. When the installation completes, run `bundle`
4. Complete the following task:

Task
-----

We have a request from a client to write the software to control the flow of planes at an airport. The planes can land and take off provided that the weather is sunny. Occasionally it may be stormy, in which case no planes can land or take off.  Here are the user stories that we worked out in collaboration with the client:

```
As an air traffic controller
So I can get passengers to a destination
I want to instruct a plane to land at an airport

As an air traffic controller
So I can get passengers on the way to their destination
I want to instruct a plane to take off from an airport and confirm that it is no longer in the airport

As an air traffic controller
To ensure safety
I want to prevent landing when the airport is full

As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate

As an air traffic controller
To ensure safety
I want to prevent takeoff when weather is stormy

As an air traffic controller
To ensure safety
I want to prevent landing when weather is stormy
```

Your task is to test drive the creation of a set of classes/modules to satisfy all the above user stories. You will need to use a random number generator to set the weather (it is normally sunny but on rare occasions it may be stormy). In your tests, you'll need to use a stub to override random weather to ensure consistent test behaviour.

Your code should defend against [edge cases](http://programmers.stackexchange.com/questions/125587/what-are-the-difference-between-an-edge-case-a-corner-case-a-base-case-and-a-b) such as inconsistent states of the system ensuring that planes can only take off from airports they are in; planes that are already flying cannot take off and/or be in an airport; planes that are landed cannot land again and must be in an airport, etc.

For overriding random weather behaviour, please read the documentation to learn how to use test doubles: https://www.relishapp.com/rspec/rspec-mocks/docs . There’s an example of using a test double to test a die that’s relevant to testing random weather in the test.

Please create separate files for every class, module and test suite.

In code review we'll be hoping to see:

* All tests passing
* High [Test coverage](https://github.com/makersacademy/course/blob/master/pills/test_coverage.md) (>95% is good)
* The code is elegant: every class has a clear responsibility, methods are short etc.

Reviewers will potentially be using this [code review rubric](docs/review.md).  Referring to this rubric in advance will make the challenge somewhat easier.  You should be the judge of how much challenge you want this weekend.

**BONUS**

* Write an RSpec **feature** test that lands and takes off a number of planes

Note that is a practice 'tech test' of the kinds that employers use to screen developer applicants.  More detailed submission requirements/guidelines are in [CONTRIBUTING.md](CONTRIBUTING.md)

Finally, don’t overcomplicate things. This task isn’t as hard as it may seem at first.

* **Submit a pull request early.**  There are various checks that happen automatically when you send a pull request.  **Fix these issues if you can**.  Green is good.

* Finally, please submit a pull request before Monday at 9am with your solution or partial solution.  However much or little amount of code you wrote please please please submit a pull request before Monday at 9am.

***Stories Completed(JavaScript)***
User story 1 - User story 1 complete. I initially tried to create the function airport.land(plane) which seemed to be working until the point where I had to push the plane into the array, so I refactored my tests to follow the walkthrough more closely and have the land function in the Plane class.

User story 2 and 3 - User story 2 and 3 complete . I implemented the same method for takeoff as I did for landing in User story 1 but in the plane class included 'this_location' which was assigned to 'airport' I also added some more tests for an error to be raised when the airport was full and when it was empty.

User story 4 - capacity - had already begun this in user story 3  but refactored code and test to include DEFAULT_CAPACITY to get rid of the magic number.

User story 5 - User story 5 completed. To pass the test,  I created a 'isStormy' function that returned false by default and created a guard clause within the 'clearForTakeoff' function that would through the error when isStormy was true. I also refactored my capacity test to have 'capacity' = 'DEFAULT_CAPACITY'.

User story 6 - User story 6 completed. I created a test similar to that in user story 5 but landing rather than takeoff and added a guard clause to the 'clearForLanding' function to make it pass. 




**Stories completed(Ruby)**

README - Refactoring
User story 2 - Refactored the plane.land test removing plane = airport.release_plane, after refactoring the test. Nested describe block for the "release_plane" method

User story 3 - Refactored test as methods takeoff and landing not needed in Plane class as they are in the Airport class. These methods have been been removed from Plane class and methods "release_plane" and "runway" have been renamed in the test and code to "takeoff" and "landing"

User story 4 - updated @plane attribute to @planes = []. Also updated test as code now contains an array. Also refactored code to include a private method for whether the airport is 'full?' or 'empty?'. Initially set capacity at 10 and then refactored test and code, adding 'DEFAULT_CAPACITY' to remove the magic number (in this case 10).Refactored again using attr_reader create a 'capacity' method and used 'initialize' to set initial value as "DEFAULT_CAPACITY". In the process of completing this story.
