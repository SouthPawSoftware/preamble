### A JavaScript Testing Framework ###

Preamble is a powerful JavaScript TDD framework backed by a powerful assertion engine that your test scripts interface with through a simple to use but powerful API. Preamble makes the task of authoring tests easy, intuitive and fun..

Documentation lives here: http://jeffschwartz.github.io/preamble/

Join the discussion here: https://groups.google.com/forum/#!forum/preamble-users/

#### v2 (Ramoth) Release Notes
This release introduces numerous new features and changes to the code base. 
Optimized, restructured and reorganized code base to provide better 
implementations, performance and ease of maintainability for the internal 
processes that Preamble performs while running tests. Also, new internal 
functionality has been added that will allow Preamble to operate and 
communicate with external processes, such as Karma, in future releases.

1) [BREAKING CHANGE] A breaking change was introduced to the layout in 
index.html, which was necessary to support in-line 
configuration. *IMPORTANT - PLEASE UPDATE EXISTING PROJECTS TO USE THE NEW 
INDEX.HTML FILE INCLUDED IN THIS RELEASE. See item 11 below.

2) [BREAKING CHANGE] Removed support for returning values from beforeEachTest 
and asyncBeforeEachTest. See item 13 below.

3) Implemented on/off/emit. Using it internally to drive tests and will be 
used in future releases for supporting Karma adapter and other external 
processes that require additional adapters. Event handlers are called 
asynchronously for improved performance.

4) Improved the reporting accuracy of the timing statistics by excluding the
elapsed times that are due to the latency from overhead (all the code that 
isn't specifically test related, such as latency incurred waiting for the 
queue to stabilize and when transitioning between test life-cycle states).

5) Reduced the latency incurred for determining when the queue has stabilized
by decreasing the delay from 500 milliseconds to 1 millisecond.

6) Added "Total elapsed time" to the report summary, which includes latency. 
See item 4 above for more information.

7) Added in-line configuration support. Tests can now configure themselves 
by including a call to either Preamble.configure or configure with a hash 
of configuration options, which will override the default configuration as 
well as any configuration options that may have been set if 
preamble-config.js was used. *IMPORTANT - USING IN-LINE CONFIGURATION TO 
OVERRIDE THE "windowGlobals" OPTION IS NOT SUPPORTED.

8) Added the showing of stack traces for all failed assertions for all 
browsers that publish either 'stack' or 'stacktrace' properties on thrown 
Error objects.

9) Added 'Hide Passed Tests' feature, including a "hidePassedTests" 
configuration property, which defaults to "false" and a check box to 
override the configuration.

10) Added configuration-based filtering. Set 1 or more filters by adding 
hashes, e.g. {group: groupLabel, test: testLabel, assertion: assertionLabel}. 
You can also use the wildcard '*' character for test and/or assertions to 
specify that all tests and/or all assertions, respectively, should be included 
in the filter.

11) Added outer wrapper div, id "preamble-ui-container", to index.html. Using
it to wrap <div id="ui-test-container" class="ui-test-container">. This was 
required in order to support in-line configuration. See item 1 above. 

12) Added display timings for groups and tests in details report.

13) Added 'passing' values from beforeEachTest and asyncBeforeEachTest to
test and asyncTest, respectively. An object is now passed as an argument to both
beforeEachTest and asyncBeforeEachTest callbacks. Properties can be set on this 
object. This same object is also passed to test and asyncTest which can access
any properties that have been set on it. See item 2 above.

