# Gradle Verification Metadata

TL;DR:

if you get an error, use this command to fix:

`./gradlew --write-verification-metadata sha256 spotlessCheck`

  

Besu uses verification metadata of dependency artifacts. If you change versions or add new dependencies, you might get a build error like this: 

```
> Could not create task ':spotlessGroovyGradleCheck'.
   > Could not create task ':spotlessGroovyGradle'.
      > Could not resolve all dependencies for configuration ':detachedConfiguration2'.
         > Dependency verification failed for configuration ':detachedConfiguration2'
           2 artifacts failed verification:
             - org.eclipse.core.expressions-3.9.0.pom (org.eclipse.platform:org.eclipse.core.expressions:3.9.0) from repository MavenRepo
             - org.eclipse.swt-3.124.0.pom (org.eclipse.platform:org.eclipse.swt:3.124.0) from repository MavenRepo
           If the artifacts are trustworthy, you will need to update the gradle/verification-metadata.xml file by following the instructions at https://docs.gradle.org/7.6/userguide/dependency_verification.html#sec:troubleshooting-verification
           
           Open this report for more details: file:///data/actions-runner/_work/besu/besu/build/reports/dependency-verification/at-16866[40](https://github.com/hyperledger/besu/actions/runs/5252337172/jobs/9488598560?pr=5588#step:4:41)985973/dependency-verification-report.html
```

use this to fix `./gradlew --write-verification-metadata sha256 spotlessCheck`

from the doc [https://docs.gradle.org/7.6/userguide/dependency\_verification.html#sub:enabling-verification](https://docs.gradle.org/7.6/userguide/dependency_verification.html#sub:enabling-verification)

  

*Full context discussion in Discord -*

*[https://discord.com/channels/905194001349627914/1118092168389742673/1118131135180976152](https://discord.com/channels/905194001349627914/1118092168389742673/1118131135180976152)*