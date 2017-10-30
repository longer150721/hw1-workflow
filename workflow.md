# <font color = "lightblue">Introduction to Git Workflow</font>
* <font size = "5" color = "lightblue"> What is Git Workflow?</font>
  + Workflow lets the publishing iteration process smoother by assigning independent branches for function development, publication, preparation and maintenance. The strict branch model also provides some very necessary structures for large projects.
  + The workflow still uses the central repository as the interactive center for all developers. Like other workflows, developers work locally and push branches into the central repository.
  + Relative to using only one master branch, the Gitflow workflow uses 2 branches to record the history of the project. The master branch stores the history of the formal publication, while the develop branch serves as an integrated branch of functionality.This makes it convenient for all submissions on the master branch to assign a version number. 
  ![image](https://sfault-image.b0.upaiyun.com/352/347/3523476139-56fea9eeb3dc3_articlex)
  + Each new function is located in one of its own branches, so that push can go to the central repository to backup and collaborateBut the functional branch does not pull out a new branch from the master branch, but uses the develop branch as the parent branch. When the new function is completed, merge back to the develop branch.New function submission should never interact directly with the master branch.
  ![image](https://sfault-image.b0.upaiyun.com/105/078/1050789629-56fea9ee44849_articlex)
  
* <font size = "5" color = "lightblue"> How to use Git Workflow?</font>
  + <font color = "#CAFFFF">Step 1：Construction of source repository</font></br>
  This step usually by the project sponsor to operate, we are here to put the administrator to PingHackers, assuming that PingHackers is for us to build a warehouse source PingHackers/git-demo, and has initiated two permanent branch of master and develop, as shown in fig.
  ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/git-demo-branch.png?_=5171187)

  + <font color = "#CAFFFF">Step 2: Developer fork source repository</font></br>
  After the establishment of the source warehouse, each development can copy a source warehouse to their own GitHub account, and then as their own development warehouse. Suppose I'm a developer in a project, I'll go to the PingHackers/git-demo project home page fork.
  ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/git-demo-fork.png?_=5171187)
  After fork, I can see a replica exactly like the source repository in my own warehouse list.
  ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/git-demo-fork-origin.png?_=5171187)

  + <font color = "#CAFFFF">Step 3: Put your own developer repository clone to local</font></br>
  It will be easy.

  + <font color = "#CAFFFF">Step 4: Building functional branches for development</font></br>
  Go into the warehouse and build the functional branch to develop and merge according to the steps of building the functional branch, so suppose I'm going to develop a "discussion" function now:
    - git checkout develop     # Switch to the develop branch     
    - git checkout -b feature-discuss     # Distinguish a functional branch  
         - touch discuss.js     # Pretending discuss.js is the function we're going to develop
         - git add   
         - git commit -m 'finish discuss feature'     # Submit changes   
    - git checkout develop     # Back to the develop branch      
    - git merge --no-ff feature-discuss     # Merge good functions into develop      
    - git branch -d feature-discuss     # Delete functional branches      
    - git push origin develop     # Submit develop to your own remote repository
  
    At this point, you go to the develop branch of your own GitHub project page to see that there is already a discuss.js file
    ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/git-demo-push.png?_=5171187)

  + <font color = "#CAFFFF">Step 5：Submit pull request to administrators</font></br>
  If I finished the "discussion" function (of course, you may also be on their develop for many times with the completion of a number of functions), after testing, found no problem, you can ask the administrator to own the warehouse develop branch merged into the develop branch of the source in the warehouse, this is pull request.
  ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/git-demo-pull-request.png?_=5171187)
  By clicking the green button on the picture above, the developer can silently wait for the administrator to submit a review to you. 
  ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/git-demo-pull-request-origin.png?_=5171187)
  + <font color = "#CAFFFF">Step 6：Administrator testing and merging</font></br>
  Next is the administrator's operation, as the administrator of the PingHackers login GitHub, you see my source warehouse launched pull request
  ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/pull-request-origin.png?_=5171187)
  What PingHackers needs to do right now is...
    - Review for my code
    - Build a new test branch in his local test
    - Determine whether to agree to merge into the develop of the source repository

  + After a tortuous journey, our discuss.js finally reached the develop branch of the source warehouse from the functional branch of my development warehouse. These are the basic steps of a git & GitHub collaboration workflow
  ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/merge.png?_=5171187)

* <font size = "5" color = "lightblue"> Why chose Git Workflow ?</font></br >
  - First of all, each development can have its own local copy of the entire project. Isolated environments allow each developer's work and other parts of the project to be modified independently.That is, free to submit to your own local repository, first completely ignore upstream development, until the convenience of the feedback back up.
  - Second, Git provides robust branching and merging models. Unlike SVN, the branch of Git is designed to be a fail safe mechanism for integrating code and sharing modifications between warehouses.



