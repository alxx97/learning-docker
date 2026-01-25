# Creating Secure Docker images

Hackers can compromise containers by bypassing the virtualization layer and gaining direct access to the container's local host.

Docker implements security processes to prevent these types of problems; however, we can add some additional security measures to make our containers less vulnerable to these attacks. This is especially important when exposing containers to the internet.

Some of these measures are:

1. Create images from trusted sources. These filters can be reviewed on Docker Hub.

2. Keep software up to date. Images with the latest updates are recommended.

3. Avoid including unnecessary packages. Install only the packages and dependencies required for the container to run.

4. Avoid running applications as the root user. The solution is to create containers that initialize with users with limited privileges.
