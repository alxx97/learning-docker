# Introduction to Docker caching

During image creation, the system keeps track of the instructions in the Dockerfile that modify the file system.

We can think of the image as a list of sequential changes to the file system, where each entry in the list corresponds to an instruction in the Dockerfile.

A **Docker layer** is defined as all the changes to the file system caused by a single instruction in the Dockerfile.

In this sense, a **Docker image** comprises all the layers created during the build process. Alternatively, it can be defined as all the changes to the file system caused by all the instructions specified in the Dockerfile.

When we run a Dockerfile that has been previously built, we may see a message like `[CACHED]` in the terminal; these are the layers that have not changed, and so instead of re-executing the instruction, the known results that have been stored are used.

Understanding caching is important for these reasons:

1. It helps us understand why images sometimes appear the same even after we've made changes and then rebuilt them.

2. It helps us write Dockerfiles, which can make changes without having to rebuild every layer. This can be achieved by ordering the Dockerfile instructions from the one that makes the fewest changes to the one that makes the most changes.
