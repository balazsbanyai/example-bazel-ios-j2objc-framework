# Task that I was trying to accomplish

I would like to build a static ios framework using java source files transpiled by j2objc. 

See `bazel build :package_ocv*`

# Expected behavior

I want the headers generated from the java sources to be included in the framework's header folder, so that the consumer of the framework can see what classes are available.

# Actual behavior

I can't get the ios_static_framework rule to include the generated headers in the produced framework.

# Description

Please provide an example where I can see how can I produce a proper ios framework including headers, using sources generated by j2objc.
