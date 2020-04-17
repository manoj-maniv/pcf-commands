# Pivotal Cloud Foundry
Commands commonly used in PCF environments

### PCF Login
Using CLI interface, login in to PCF environment using the below command. If API endpoint is required, provide **https://api.run.pivotal.io**.

```cf login```
##### Sample Result

```D:\Workout_Projects\pcf-rest-demo>cf login
API endpoint: https://api.run.pivotal.io

Email: email@gmail.com
Password:
Authenticating...
OK

Targeted org email-org
Targeted space development

API endpoint:   https://api.run.pivotal.io (API version: 3.81.0)
User:           email@gmail.com
Org:            email-org
Space:          development
```

### Push Java application

Command to Push Java application into PCF environment

```cf push pcf-rest-demo-0.0.1-SNAPSHOT -p build\libs\pcf-rest-demo-0.0.1-SNAPSHOT.jar --random-route ```

##### Sample Result

```
Pushing app pcf-rest-demo-0.0.1-SNAPSHOT to org manoemails-org / space development as manoemails@gmail.com...
Getting app info...
Creating app with these attributes...
+ name:       pcf-rest-demo-0.0.1-SNAPSHOT
  path:       D:\Workout_Projects\pcf-rest-demo\build\libs\pcf-rest-demo-0.0.1-SNAPSHOT.jar
  routes:
+   pcf-rest-demo-001-snapshot-appreciative-eland-re.cfapps.io

Creating app pcf-rest-demo-0.0.1-SNAPSHOT...
Mapping routes...
Comparing local files to remote cache...
Packaging files to upload...
Uploading files...
 289.16 KiB / 289.16 KiB [=================================================================================================================================] 100.00% 7s

Waiting for API to complete processing files...

Staging app and tracing logs...
   Downloading web_config_transform_buildpack...
   Downloading ruby_buildpack...
   Downloading dotnet_core_buildpack...
   Downloading staticfile_buildpack...
   Downloading nodejs_buildpack...
   Downloaded ruby_buildpack
   Downloading go_buildpack...
   Downloaded nodejs_buildpack
   Downloading java_buildpack...
   Downloaded dotnet_core_buildpack
   Downloading python_buildpack...
   Downloading binary_buildpack...
   Downloaded java_buildpack
   Downloading dotnet_core_buildpack_beta...
   Downloaded staticfile_buildpack
   Downloading php_buildpack...
   Downloaded go_buildpack
   Downloaded python_buildpack
   Downloaded binary_buildpack
   Downloaded php_buildpack
   Downloaded dotnet_core_buildpack_beta
   Cell e210786d-5a4b-44cc-9b59-e574f91e8fbb creating container for instance 47559995-721a-4968-abb4-2e0c3e33327c
   Cell e210786d-5a4b-44cc-9b59-e574f91e8fbb successfully created container for instance 47559995-721a-4968-abb4-2e0c3e33327c
   Downloading app package...
   Downloaded app package (15M)
   -----> Java Buildpack v4.26 (offline) | https://github.com/cloudfoundry/java-buildpack.git#e06e00b
   -----> Downloading Jvmkill Agent 1.16.0_RELEASE from https://java-buildpack.cloudfoundry.org/jvmkill/bionic/x86_64/jvmkill-1.16.0-RELEASE.so (found in cache)
   -----> Downloading Open Jdk JRE 1.8.0_232 from https://java-buildpack.cloudfoundry.org/openjdk/bionic/x86_64/openjdk-jre-1.8.0_232-bionic.tar.gz (found in cache)
          Expanding Open Jdk JRE to .java-buildpack/open_jdk_jre (1.8s)
          JVM DNS caching disabled in lieu of BOSH DNS caching
   -----> Downloading Open JDK Like Memory Calculator 3.13.0_RELEASE from https://java-buildpack.cloudfoundry.org/memory-calculator/bionic/x86_64/memory-calculator-3.13.0-RELEASE.tar.gz (found in cache)
          Loaded Classes: 11884, Threads: 250
   -----> Downloading Client Certificate Mapper 1.11.0_RELEASE from https://java-buildpack.cloudfoundry.org/client-certificate-mapper/client-certificate-mapper-1.11.0-RELEASE.jar (found in cache)
   -----> Downloading Container Security Provider 1.16.0_RELEASE from https://java-buildpack.cloudfoundry.org/container-security-provider/container-security-provider-1.16.0-RELEASE.jar (found in cache)
   -----> Downloading Spring Auto Reconfiguration 2.11.0_RELEASE from https://java-buildpack.cloudfoundry.org/auto-reconfiguration/auto-reconfiguration-2.11.0-RELEASE.jar (found in cache)
   Exit status 0
   Uploading droplet, build artifacts cache...
   Uploading droplet...
   Uploading build artifacts cache...
   Uploaded build artifacts cache (129B)
   Uploaded droplet (57.2M)
   Uploading complete
   Cell e210786d-5a4b-44cc-9b59-e574f91e8fbb stopping instance 47559995-721a-4968-abb4-2e0c3e33327c
   Cell e210786d-5a4b-44cc-9b59-e574f91e8fbb destroying container for instance 47559995-721a-4968-abb4-2e0c3e33327c
   Cell e210786d-5a4b-44cc-9b59-e574f91e8fbb successfully destroyed container for instance 47559995-721a-4968-abb4-2e0c3e33327c

Waiting for app to start...

name:              pcf-rest-demo-0.0.1-SNAPSHOT
requested state:   started
routes:            pcf-rest-demo-001-snapshot-appreciative-eland-re.cfapps.io
last uploaded:     Fri 20 Mar 23:14:32 IST 2020
stack:             cflinuxfs3
buildpacks:        client-certificate-mapper=1.11.0_RELEASE container-security-provider=1.16.0_RELEASE
                   java-buildpack=v4.26-offline-https://github.com/cloudfoundry/java-buildpack.git#e06e00b java-main java-opts java-security
                   jvmkill-agent=1.16.0_RELEASE open-jdk...

type:            web
instances:       1/1
memory usage:    1024M
start command:   JAVA_OPTS="-agentpath:$PWD/.java-buildpack/open_jdk_jre/bin/jvmkill-1.16.0_RELEASE=printHeapHistogram=1 -Djava.io.tmpdir=$TMPDIR
                 -XX:ActiveProcessorCount=$(nproc) -Djava.ext.dirs=$PWD/.java-buildpack/container_security_provider:$PWD/.java-buildpack/open_jdk_jre/lib/ext
                 -Djava.security.properties=$PWD/.java-buildpack/java_security/java.security $JAVA_OPTS" &&
                 CALCULATED_MEMORY=$($PWD/.java-buildpack/open_jdk_jre/bin/java-buildpack-memory-calculator-3.13.0_RELEASE -totMemory=$MEMORY_LIMIT -loadedClasses=12665
                 -poolType=metaspace -stackThreads=250 -vmOptions="$JAVA_OPTS") && echo JVM Memory Configuration: $CALCULATED_MEMORY && JAVA_OPTS="$JAVA_OPTS
                 $CALCULATED_MEMORY" && MALLOC_ARENA_MAX=2 SERVER_PORT=$PORT eval exec $PWD/.java-buildpack/open_jdk_jre/bin/java $JAVA_OPTS -cp $PWD/.
                 org.springframework.boot.loader.JarLauncher
     state     since                  cpu    memory         disk           details
#0   running   2020-03-20T17:44:54Z   0.0%   139.8M of 1G   125.7M of 1G
```
