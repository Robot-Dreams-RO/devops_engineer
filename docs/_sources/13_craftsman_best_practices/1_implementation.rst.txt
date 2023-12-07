###################
13.1 Implementation
###################

====================================================
1. Business logic should be the LAST thing you write
====================================================

========================
2. Paper before keyboard
========================

There's always the temptation to just start building things, but the truth is that's actually counter productive

#. First, write down how the data structures should look like (payload, tables), try to visualize the system
#. If needed, build or draw some diagrams about how the systems will communicate (no need to specify at an API level)
#. Only then, when you've agreed upon a general structure of the implementation do you get to actually start working on it

================================================
3. Tests, tests, tests ... did I mention tests ?
================================================

.. note::

    It doesn't matter how mature you are as a programmer or how good you are. Your level of maturity and expertise in software development is determined and reflected by your relationship with tests

#. There are many flavours of tests :: Unit tests / Integration tests or System tests / End to end tests
#. NO, it's not QA's job to test your code. It's your job. The Wright brothers flew their own plane, they didn't have someone else do it for them
#. Write green tests but also red tests
#. Are you writing an API ? Have you made sure to add tests that check the payload ? Verify not only the presence of fields, but also lack of others, to make sure the contract is sound
#. Don't rely only on unit tests. It's tempting to write only these, 'cause they're faster. However, they don't interact with the entire system. A unit test checks that your new Tesla has a fancy custom horn but an integration test discovers the system is built wrongly and it consumes 1% battery everyday
#. You should have 99 problems but the tests shouldn't be one. You wrote a feature. Did you cover it with tests ? You fixed a bug. Do you have a test to check for regression ? You refactored some code. Is it covered by a test ?

=================================================================================
4. Plan each step, have it ready in your mind before it comes ouf of your fingers
=================================================================================

#. One of the best methodologies you can implement is TDD (Test Driven Development). This links strongly with the previous segment
#. It will help you by having your checks ready before you write any piece of code
#. Are you building an API ? Then, first write tests to ensure the contract, then actually build the API
