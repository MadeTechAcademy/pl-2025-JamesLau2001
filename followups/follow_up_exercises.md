# Follow up Exercises

## Tasks

1. Explain how code on your delivery is packaged and deployed.
2. Explain what you understand of the approach to hosting apps in the course.
3. How does this differ from approaches you've used before? What's the impact of changing our mind? and the benefits?
4. Explain the troubleshooting steps you would use on a failing pipeline, either those you learned on this course or those you have used on your delivery.
5. Identify a problem or improvement you could do on a pipeline on your delivery. What did your team decide to do to fix or improve it (even if it hasn't been prioritised yet)?

## Stretch task
1. Terraform resources to build docker images and push them to ECR is not the only way, it's not even the most usual way using github actions! Try out a new pipeline with different github actions to build and deploy the ex 6 image to the ex 6 ECR. You could start from your ex 3 pipeline syntax to build and test the node code first.
2. If you identified a different approach to hosting apps containers, investigate more and explain your discovered new approach including, what are the pros and cons of adopting it, if our start point is where the course examples left off?


## Add your answers here, or in this folder
1.
I think in my project, only the CI is set up. We have a ci.yml file, which runs a couple of bash script without any cloud connections. Right now, the following steps are taken:
- Checks out the code
- Sets up python
- Frees disk space
- Creates the .env files
- Installs dependency management (Poetry)
- Installs dependencies
- Build containers
- Formatting
- Sort imports alphabetically and automatically separating them into sections and by type
- Linting
- Checks for missing django migrations
- Applies migrations
- Runs tests
To summarise, it sets up the environment, builds the app, then runs tests.

2.
We separate hosting into CI and CD.
- CI refers to the GitHub actions, and includes criteria that must pass in order to move onto CD. However, it first must set up the environment, and builds the app. An example of passing criteria could be passing tests first
- CD refers to actually deploying the app, for example, using services like AWS and Terraform.

3.
I always assumed that all jobs/runners should pass in a pipeline. However, I now understand that this isn't always required, and sometimes it's even desirable. We are able to continue working on other features, but by failing tests remind engineers to go back and fix faulty parts of code.

4.
*One key thing to remember is that fixing one problem doesn't guarantee the entire issue is fixed
- Start by reading the error messages from the logs in GitHub actions
- Zone in on the error, and fix the issue based on what is outputted
- I would use the AWS console to find missing variables and/or secrets
- After fixing this, I would run the pipeline again, and reading the logs again, repeating until the overall pipeline passes

5.
Right now, it seems that my delivery includes formatting and linting in the pipeline. Formatting and linting aid in overall human readability, but is not required in the pipeline as the pipeline is not human. To counter this, I would just make it best practice to format/lint before commits. 