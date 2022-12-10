The typedb-runner artifacts are not published. These are the steps I use to build and
host for my team.  

I am unfamiliar with bazel and of course do not have access to publish to vaticle's repositories so this
work is just a hack to get the jars built and published somewhere.  

The process is the following...  

First build,
```
bazel build //
bazel build //test
```

Next, run the `assemble-maven` target.
```
bazel build //:assemble-maven
bazel build //test:assemble-maven
```

NOTE (nphair): I am not sure if running assemble-maven will also run the build.  

Then, copy the `deploy-maven-deploy.py*` script at the top-level of the repo into
the `bazel-bin/test` directory. Run the script. It's a hack of the original
to get the local files and there upload location. With this info, copy
the local files to your destination. I am hosting on [my site][1] for my team.   


[1]: https://www.cs.virginia.edu/~np4ay/repo/com/vaticle/typedb/typedb-runner/2.12.0-SNAPSHOT/
