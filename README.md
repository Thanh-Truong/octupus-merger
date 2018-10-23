# octupus-merger
A helper project to allow pulling code from different branches, packing them to be run on a selected environment

# Motivations

We need to rethink our CI strategy for [Apache Airflow](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwiLyr2otJzeAhWIzKQKHWt0DBsQFjAAegQICRAB&url=https%3A%2F%2Fairflow.apache.org%2F&usg=AOvVaw388kHRAT6nV9AH5zbkuDlv), which was deployed on `prod` (production) and `staging` (staging) environment hosted on GCP.

According to [ELT best practices with Airflow](https://gtoonstra.github.io/etl-with-airflow/deployments.html#continuous-integration), it says  

> The suggested CI model requires at least two pipelines to be set up:
> A pipeline that compiles and deploys the ‘core’ platform with all the hooks, operators and generic function of your airflow installation. This pipeline would draw code from a code repository, build a docker image from the code and make that typically available from a registry somewhere. You’d probably develop and test the hooks on a local development machine somewhere (as per the other tips on keeping your development infrastructure small). Then you could have a setup where certain branches are merged to compile an “acceptance image” that is deployed and used on the acceptance environment and a final “master” branch image build that is only deployed on production.
> Another pipeline to manage DAG deployments (on the shared file system) that might use branches or combinations of branches to test the impact of changing queries, DAGS and other code.

In order to merging branches, Git has support for [Octupus merge mode](http://www.freblogg.com/2016/12/git-octopus-merge.html), which is not sufficient enough in case of merge failures or if there is need for more configurations: which branches should be included, or excluded. Thus, a developer at Atlassian has written up a nice article and a tool [here](https://developer.atlassian.com/blog/2015/01/git-merge-distinct-octopus-merge/)

This project is an exercise to study what features (needs) that such tool should have. In other words, it is a protoype, proof of concepts, as a mean of decision making.

# TODOs
- [ ] Add instructions on how to use
- [ ] Rewrite the scripts to Python code
