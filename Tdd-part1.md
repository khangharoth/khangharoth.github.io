## TDD - The Unfulfilled promise: Part 1

Why is TDD still mandated and not practised in most of the teams/organizations ground up?

A typical experience is that teams practise this for some time (six months to a year) and then give up on it. This shouldn't be happening, as the whole premise was that once the team starts doing TDD, they will see the benefits and would never go back.

What’s the reason for this peculiar phenomenon? In my experience, it's down to the benefits which were promised but never materialized for the individuals or teams.


Again, why are the developers/teams not getting the promised benefits that are so widely discussed and agreed upon?

Let’s look for more detail. One of the biggest challenges faced by the team is the inability to maintain the test suite over the life cycle of the project. In the beginning, with few tests and a small code base, tdd seems to be working and teams thought they were on the right track. Over time some common issues occur which makes the whole premise of the said benefits questionable.

So what are these problems?

- Difficult to understand the intent: Yes, the tests failed, but it’s really hard to understand the intent of those tests and hence no real value add in case of failures. What’s under test is not easy to understand and it defeats the whole purpose of having tests in the first place.
- Increase in build time: Applications grow and so did the number of tests and pretty soon the build takes more than 10 min (a high threshold for the good test suite) and this time starts adding for every check-in and slows the overall process down. Key reasons for the increase in build time are
𝘈𝘵𝘵𝘢𝘤𝘩𝘮𝘦𝘯𝘵 𝘵𝘰 𝘵𝘩𝘦 𝘦𝘹𝘪𝘴𝘵𝘪𝘯𝘨 𝘛𝘦𝘴𝘵𝘴: 𝘋𝘦𝘷𝘦𝘭𝘰𝘱𝘦𝘳𝘴 𝘴𝘦𝘦 𝘵𝘩𝘦 𝘵𝘦𝘴𝘵𝘴 𝘢𝘴 𝘴𝘰𝘮𝘦 𝘴𝘰𝘳𝘵 𝘰𝘧 𝘪𝘯𝘷𝘦𝘴𝘵𝘮𝘦𝘯𝘵 𝘢𝘯𝘥 𝘩𝘦𝘯𝘤𝘦 𝘯𝘦𝘷𝘦𝘳 𝘥𝘦𝘭𝘦𝘵𝘦𝘴 𝘰𝘭𝘥/𝘰𝘣𝘴𝘰𝘭𝘦𝘵𝘦/𝘳𝘦𝘱𝘦𝘢𝘵𝘦𝘥 𝘵𝘦𝘴𝘵 𝘤𝘢𝘴𝘦𝘴.  
𝘚𝘭𝘰𝘸 𝘛𝘦𝘴𝘵𝘴: 𝘛𝘦𝘴𝘵𝘴 𝘵𝘢𝘬𝘪𝘯𝘨 𝘢 𝘴𝘦𝘤 to run 𝘭𝘰𝘰𝘬𝘴 𝘧𝘢𝘴𝘵 𝘣𝘶𝘵 𝘢𝘳𝘦 indeed𝘷𝘦𝘳𝘺 𝘴𝘭𝘰𝘸. 1000 𝘴𝘶𝘤𝘩 𝘵𝘦𝘴𝘵 𝘤𝘢𝘴𝘦𝘴 𝘸𝘰𝘶𝘭𝘥 𝘵𝘢𝘬𝘦 𝘤𝘭𝘰𝘴𝘦 𝘵𝘰 16 𝘮𝘪𝘯 𝘵𝘰 𝘳𝘶𝘯.
𝘕𝘰𝘵 𝘢𝘣𝘭𝘦 𝘵𝘰 𝘳𝘶𝘯 𝘪𝘯 𝘗𝘢𝘳𝘢𝘭𝘭𝘦𝘭: 𝘐𝘯 𝘭𝘢𝘳𝘨𝘦 𝘱𝘳𝘰𝘫𝘦𝘤𝘵𝘴 𝘸𝘪𝘵𝘩 𝘮𝘰𝘳𝘦 𝘵𝘩𝘢𝘯 20𝘒+ 𝘵𝘦𝘴𝘵𝘴, 𝘵𝘩𝘦 𝘵𝘦𝘢𝘮 𝘸𝘪𝘭𝘭 𝘩𝘢𝘷𝘦 𝘵𝘰 𝘳𝘦𝘭𝘺 𝘰𝘯 𝘵𝘩𝘦 𝘢𝘣𝘪𝘭𝘪𝘵𝘺 𝘵𝘰 𝘳𝘶𝘯 𝘵𝘩𝘦 𝘸𝘩𝘰𝘭𝘦 𝘵𝘦𝘴𝘵 𝘴𝘶𝘪𝘵𝘦 𝘪𝘯 𝘱𝘢𝘳𝘢𝘭𝘭𝘦𝘭.
- Randomness in tests: Test fails randomly i.e on rerun the build passes and the team members gets into the habit of running the build again. Rather than fixing the underlying issues, randomness adds over time and the test suite becomes more like a coin toss, rather than a tool to give feedback.
Long time to fix build failures: Due to the randomness, team members are not sure if the build is failing because of a new change, or it's down to randomness and this leads to red builds for long before a team members take a look.
Checkin on Red builds: As red build becomes the norm so is check-in on already failed build and from there it's all downhill.
Tests interfering with the refactoring: Tests written after the code is written, typically exhibit this problem, where the coupling between the test and code is very high.
𝘐𝘯𝘢𝘥𝘷𝘦𝘳𝘵𝘦𝘯𝘵𝘭𝘺 𝘵𝘩𝘦 𝘵𝘦𝘴𝘵 𝘪𝘴 𝘵𝘦𝘴𝘵𝘪𝘯𝘨 𝘵𝘩𝘦 𝘪𝘮𝘱𝘭𝘦𝘮𝘦𝘯𝘵𝘢𝘵𝘪𝘰𝘯 𝘥𝘦𝘵𝘢𝘪𝘭 𝘢𝘯𝘥 𝘯𝘰𝘵 𝘵𝘩𝘦 𝘧𝘶𝘯𝘤𝘵𝘪𝘰𝘯𝘢𝘭𝘪𝘵𝘺 𝘢𝘯𝘥 𝘵𝘩𝘪𝘴 𝘭𝘦𝘢𝘥𝘴 𝘵𝘰 𝘵𝘪𝘨𝘩𝘵 𝘤𝘰𝘶𝘱𝘭𝘪𝘯𝘨.
𝘛𝘦𝘴𝘵𝘴, 𝘸𝘩𝘦𝘳𝘦 𝘮𝘰𝘤𝘬𝘪𝘯𝘨 𝘪𝘴 𝘩𝘦𝘢𝘷𝘪𝘭𝘺 𝘶𝘴𝘦𝘥, 𝘤𝘢𝘯 𝘣𝘦𝘤𝘰𝘮𝘦 𝘷𝘦𝘳𝘺 𝘣𝘳𝘪𝘵𝘵𝘭𝘦 𝘸𝘩𝘦𝘯 𝘥𝘦𝘷𝘦𝘭𝘰𝘱𝘦𝘳𝘴 𝘫𝘶𝘴𝘵 𝘸𝘢𝘯𝘵 𝘵𝘰 𝘳𝘦𝘧𝘢𝘤𝘵𝘰𝘳 𝘵𝘩𝘦 𝘴𝘩𝘢𝘱𝘦 𝘰𝘧 𝘵𝘩𝘦 𝘤𝘰𝘥𝘦. 𝘈𝘭𝘭 𝘵𝘩𝘰𝘴𝘦 𝘷𝘦𝘳𝘪𝘧𝘪𝘤𝘢𝘵𝘪𝘰𝘯𝘴 𝘢𝘳𝘰𝘶𝘯𝘥 𝘩𝘰𝘸 𝘮𝘢𝘯𝘺 𝘵𝘪𝘮𝘦𝘴 𝘢 𝘨𝘪𝘷𝘦𝘯 𝘤𝘰𝘭𝘭𝘢𝘣𝘰𝘳𝘢𝘵𝘰𝘳 𝘪𝘴 𝘤𝘢𝘭𝘭𝘦𝘥 𝘪𝘯𝘧𝘭𝘰𝘸 𝘣𝘦𝘤𝘰𝘮𝘦 𝘷𝘦𝘳𝘺 𝘴𝘦𝘯𝘴𝘪𝘵𝘪𝘷𝘦 𝘵𝘰 𝘴𝘮𝘢𝘭𝘭 𝘤𝘩𝘢𝘯𝘨𝘦𝘴 𝘪𝘯 𝘵𝘩𝘦 𝘴𝘵𝘳𝘶𝘤𝘵𝘶𝘳𝘦 𝘰𝘧 𝘵𝘩𝘦 𝘤𝘰𝘥𝘦.
- Over Testing: Testing is done in layers, where the outer layer test tries to test the whole internal implementation ex: DAO Test, Services Test, Functional Test & then End to End Test. This results in a common internal codebase (DAO layer) being covered by many-many tests and hence any change there can result in lots of failing tests. Ideally, any part of code should be covered by two tests, one is unit and another End-to-End and hence any change should only result in two failing tests.
- Individuals not committed to TDD philosophy: TDD is a team sport and hence everyone in the team needs to adhere to the philosophy of writing tests first and then continuous refactoring. Even one member, not following these guidelines can create the above-mentioned problems for the entire team.
