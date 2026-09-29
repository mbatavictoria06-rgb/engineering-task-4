Task 4 — Code Review Retrospective

1. Best Comment Received

The best comment I received was the comment pointing out the duplicate url property in src/prisma/db.ts. The reviewer noticed that both the original process.env['DATABASE_URL']! and the new validated databaseUrl were being passed as url properties. This helped me understand the importance of carefully checking the final state of a file after making changes, especially when updating configuration objects.

2. Best Comment Given

The best comment I gave was on the shutdown-handling PR. I noticed that the verification script assumed claimJobs(2) would return the two jobs created specifically for the test. I reproduced the issue by running the documented verification command and found that unrelated pending jobs could be claimed first, causing the verification to fail. This taught me to test not only the main implementation but also whether verification scripts themselves are deterministic and isolated.

3. Something I Caught in Someone Else’s Code That I Have Also Done

One thing I noticed during the reviews was the importance of testing edge cases and failure scenarios. For example, I identified a NUL/control-character validation issue in the gig search implementation and also recognized that my own PR did not yet have a specific automated test for a missing DATABASE_URL. This reminded me that happy-path testing is not enough; configuration failures and unusual inputs should also be considered.

4. What I Will Change About How I Write PRs

After reviewing three different PRs, I will make my own PRs easier for another developer to verify. I will keep changes focused, clearly explain why a change is being made, and include tests for both expected behaviour and important edge cases. I will also pay more attention to deterministic verification, clear configuration requirements, and the final diff before requesting review.
