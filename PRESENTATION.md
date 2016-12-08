
## Travis CI

Following the instructions in the blog post below, one can easily add a
repository with C++ code, CMake and ctest to Travis CI.

http://genbattle.bitbucket.org/blog/2016/01/17/c++-travis-ci/

It will build all branches, so you can choose which ones you would like
to be monitored by Travis CI following the instructions in the post below.

https://blog.travis-ci.com/2012-08-13-build-workflow-around-pull-requests/

Travis CI does not support MPI out of the box. But you can install MPI during the build.
The JuliaParallel project does that actually, so you can just adapt to your
needs... except that some times it fails for your project or environment.

```
E: Unable to locate package libmpich10

E: Package 'libmpich-dev' has no installation candidate

The command "sh ./conf/travis-install-mpi.sh $MPI_IMPL" failed and exited with 100 during .
```

https://github.com/JuliaParallel/MPI.jl/blob/master/.travis.yml

Here's a more complex build with Travis CI.

https://github.com/mpi4py/mpi4py/blob/master/.travis.yml

Example project in C, that is moving to Jenkins.

https://github.com/hbowden/nextgen
https://github.com/hbowden/nextgen/issues/3

## Jenkins CI

For Jenkins, you will need to tell ctest to output an XML. Jenkins will be
expecting a JUnit XML, but ctest emits a different XML. So instead of the
default test parser, which comes with Jenkins, we need a plug-in that
understands the format created by ctest: xUnit plug-in.

https://wiki.jenkins-ci.org/display/JENKINS/xUnit+Plugin

And to tell ctest to output an XML, you can follow this StackOverflow
answer instructions.

stackoverflow.com/questions/21633716/producing-ctest-results-in-jenkins-xunit-1-58/21688776#21688776

