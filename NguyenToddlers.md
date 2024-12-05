links: 
https://pagure.io/fedora-infra/toddlers/blob/main/f/toddlers/plugins/check_email_overrides.py

https://pagure.io/fedora-infra/toddlers/blob/main/f/toddlers/plugins/check_commit_rights.py

## check_commit_rights.py
    - Takes in fedmsg messages under 'toddlers.trigger.check_commit_rights' as input and searches for any user not part of that group but still have commit rights.
    - accept_topics
        - boolean val to check if toddler is interested in specific topic
    - process
        - checks if user has commit rights
        - Loops through users with group owner, admin, collaborator, commit
            - These groups have commit rights
        - Checks for users that are not apart of exclude_list or packagers group
        - Adds these users to not_packagers
        - Logs all users not apart of not_packagers
        - still have to check rights periodically, users that have been removed / removed themselves could still be in users_list
        - finds users with email notifications on and sends them an email

## check_email_overrides.py
    - Takes in fedmsg messages under 'toddlers.trigger.packager_bugzilla_sync' and runs sync of all packagers found in FAS (what is FAS) to bugzilla so they can edit flags on Fedora tickets
    - accept_topics
        - boolean val to check if toddler is interested in specific topic, same as check_commit_rights.py
    - process
        - parses email_overrides.toml
            - parsing for FAS / bugzilla accounts 
        - establshing connections to FAS / bugzilla
        - Validates emails to match usernames
            - If does not match, maps them to 'logs' list
        - Notifies admin with 'logs' list

## running compose-tracker
    - using tox
    - Passed all test, 3 warnings in test_consumer.py
    - Not to sure what the goal of test_cosumer.py was



