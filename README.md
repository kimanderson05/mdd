#To deploy to the Staging Server Strict adherence to the following process is required.
1. **Merge Dev Branch into Master**
Upon completion of fully testing a new feature in your local dev environment merge the kaTesting branch back into master. To do this successfully you will need to first pull the remote master branch, ensuring your local master branch is up to date.
    1. $ git checkout master
        * Switches to the local master branch
    2. $ git pull github master
        * github is the name of the remote repo we will use to differentiate between our other remote deployment servers
        * Resolve any conflicts
        * Visit each conflicted file and resolve any conflicts. Save files.
        * Once conflicts are resolved and saved, commit changes and pull remote master branch again.
            1. $ git add -A
            1. $ git commit -am (Relevant detailed commit message.)
            1. $ git pull github master
..3. $ git merge kaTesting
..* Resolve any conflicts (see 2.2.1)
..4. **Test**
You have just altered the code base since you last tested your new feature; additionally you might have broken someone else's recent addition, congratulations! Take some time to work through and test out every aspect of your new feature.
..* If any of your tests fail, the master branch is flawed and not ready to be pushed to remote. Resolve the issues prior to pushing to the remote in the next step.
5. $ git push github master 
..* Push your changes up to the shared repo so that other devs can react to the latest changes to the project codebase.
2. **Tag Your Release**
Not every commit is equal. Through the dev process many commits will take place, but when releasing a new feature the commit that is merged and promoted live is more significant than others. By tagging this fully merged commit we are able to diagnose issues or discuss a specific version of the project. 
..* $ git tag -a vX.X.X -m 'Release Code or Feature Name'
..1. X.X.X should be an incriminated according to the Versions Numbering Development Policy (ex: FileName-v4.1.1).
..* $ git push github --tags
..1. Tags are not automatically pushed in a normal push, they must be manually pushed to the remote repo.
3. **Communicate with your Team**
Announce to your team that you are about to change the staging server. If someone else is currently testing on the staging server you will need to coordinate for when you can promote your code in the next step. 
..* Verify the testing of the last feature to be promoted has completed.
4. **Promote to Staging**
Promote your tested code to the staging environment to ensure stability within the overall system. 
..* $ git push staging master
..1. staging is linked to the --remote staging heroku server
5. **Test Again!**
If anything fails, try to replicate the issue within your Local Dev Environment. Should the issue not be replicable there identify why it isn't working in Staging and attempt to solve the problem.
6. **Communicate Successful Promotion of New Feature**
Brag a little about how sweet your new feature is! Ideally this will promote other users to try it out thereby testing it further prior to going live in production. 
..* Use the hastag #newFeatureStaged in the #staging_dwp channel. Identify the name of your feature, that it has been completed, and any info on how to use it.
..* When the scheduled promotion of Staging to Production occurs you will need to test every feature that has been recently staged to make sure that your co-workers have not modified the feature in any way.

