# Step 1 - Run the project outside Docker

* [Official Source](https://docs.docker.com/language/java/build-images/)

## Get the project source code

* Clone the repo

```
git clone https://github.com/spring-projects/spring-petclinic.git
```

* Read carefully the readme file

<!---->

* [ ] What type of application is it ? (A Java Application using Spring)
* [ ] Which database engine is used ? (A in-memory database H2 which gets populated at startup with data.)
* [ ] Do we need to install the package manager _MAVEN_ before building the project ? ()

<!---->

* Inspect the dependencies (pom.xml)

<!---->

* [ ] Which version of Java should compatible with the code provided ?

## Setup Java components

### Check your current java installation

* [ ] Where is java installed ?

```
[INPUT]
which java 

[OUTPUT]
/Users/yannmenoud/.jenv/shims/java
```

* [ ] Which current compiler is installed (JDK) ?

```
[INPUT]
java --version

[OUTPUT]
openjdk 20.0.1 2023-04-18
```

* [ ] Which current runtime is installed (JRE) ?

```
[INPUT]
java --version

[OUTPUT]
OpenJDK Runtime Environment (build 20.0.1+9-29)
```

* [ ] Do we need to install the java virtual machine (JVM) ?
```
No, already included in JRE

```

### Install the Open JDK

* [Oracle Download Web Site](https://jdk.java.net/20/)

{% hint style="info" %}
* Accept the end user license before trying, then
* Then get the target url (cookies.
{% endhint %}

```
[INPUT]
curl -O "https://download.java.net/java/GA/jdk20.0.1/b4887098932d415489976708ad6d1a4b/9/GPL/openjdk-20.0.1_macos-aarch64_bin.tar.gz"

[OUTPUT]
 % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  183M  100  183M    0     0  3511k      0  0:00:53  0:00:53 --:--:-- 3450k
```

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Powershell output during sdk download process</p></figcaption></figure>

#### Check the archive integrity before installing the JDK

* [Get the hash provided by Oracle](https://download.java.net/java/GA/jdk20.0.1/b4887098932d415489976708ad6d1a4b/9/GPL/openjdk-20.0.1\_windows-x64\_bin.zip.sha256)
* Generate your local hash based on the archive downloaded ([help](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.3))
* Compare both hashes...

```
[INPUT]
shasum -a 256 ~/Downloads/openjdk-20.0.1_macos-aarch64_bin.tar.gz

Result:  78ae5bb4c96632df8d3f776919c95653d1afd3e715981c4d33be5b3c81d05420

[OUTPUT]
78ae5bb4c96632df8d3f776919c95653d1afd3e715981c4d33be5b3c81d05420  /Users/yannmenoud/Downloads/openjdk-20.0.1_macos-aarch64_bin.tar.gz
```
It's a match !

#### Unzip jdk archive

```
[INPUT]
tar -x openjdk-20.0.1_macos-aarch64_bin.tar.gz

[OUTPUT]
x ./
x ./jdk-20.0.1.jdk/
x ./jdk-20.0.1.jdk/Contents/
x ./jdk-20.0.1.jdk/Contents/CodeResources
x ./jdk-20.0.1.jdk/Contents/_CodeSignature/
x ./jdk-20.0.1.jdk/Contents/Home/
x ./jdk-20.0.1.jdk/Contents/MacOS/
x ./jdk-20.0.1.jdk/Contents/Info.plist
x ./jdk-20.0.1.jdk/Contents/MacOS/libjli.dylib
x ./jdk-20.0.1.jdk/Contents/Home/bin/
x ./jdk-20.0.1.jdk/Contents/Home/include/
x ./jdk-20.0.1.jdk/Contents/Home/release
x ./jdk-20.0.1.jdk/Contents/Home/lib/
x ./jdk-20.0.1.jdk/Contents/Home/legal/
x ./jdk-20.0.1.jdk/Contents/Home/conf/
x ./jdk-20.0.1.jdk/Contents/Home/jmods/
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.security.sasl.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jartool.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.se.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.zipfs.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jdeps.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jstatd.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jdwp.agent.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.sql.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.smartcardio.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.hotspot.agent.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.internal.jvmstat.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.compiler.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.incubator.vector.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.sql.rowset.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jfr.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jpackage.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.crypto.cryptoki.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.internal.vm.compiler.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.unsupported.desktop.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.management.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.rmi.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.management.jfr.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.sctp.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.security.jgss.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.internal.vm.compiler.management.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.net.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.prefs.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.logging.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.xml.dom.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.base.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.xml.crypto.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.naming.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.internal.ed.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.naming.dns.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.datatransfer.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.unsupported.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jlink.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.charsets.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.localedata.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jcmd.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.desktop.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.accessibility.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.attach.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.management.rmi.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.incubator.concurrent.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.transaction.xa.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jshell.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.xml.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.management.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.internal.opt.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.httpserver.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.net.http.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.random.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.compiler.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.internal.le.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.instrument.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.dynalink.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.management.agent.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.internal.vm.ci.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.security.auth.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.scripting.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jdi.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.crypto.ec.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.naming.rmi.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jconsole.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.javadoc.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.editpad.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.jsobject.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/java.security.jgss.jmod
x ./jdk-20.0.1.jdk/Contents/Home/jmods/jdk.nio.mapmode.jmod
x ./jdk-20.0.1.jdk/Contents/Home/conf/logging.properties
x ./jdk-20.0.1.jdk/Contents/Home/conf/sound.properties
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/
x ./jdk-20.0.1.jdk/Contents/Home/conf/net.properties
x ./jdk-20.0.1.jdk/Contents/Home/conf/management/
x ./jdk-20.0.1.jdk/Contents/Home/conf/management/jmxremote.access
x ./jdk-20.0.1.jdk/Contents/Home/conf/management/management.properties
x ./jdk-20.0.1.jdk/Contents/Home/conf/management/jmxremote.password.template
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/java.security
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/java.policy
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/unlimited/
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/README.txt
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/limited/
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/limited/default_US_export.policy
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/limited/exempt_local.policy
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/limited/default_local.policy
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/unlimited/default_US_export.policy
x ./jdk-20.0.1.jdk/Contents/Home/conf/security/policy/unlimited/default_local.policy
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management.rmi/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported.desktop/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler.management/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.se/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.jgss/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jfr/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.sasl/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.net/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jsobject/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.zipfs/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.vector/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.dynalink/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.compiler/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jcmd/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.dns/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.instrument/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.localedata/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.rmi/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.compiler/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.prefs/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.cryptoki/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.editpad/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.logging/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.net.http/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jpackage/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.opt/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jconsole/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql.rowset/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.jgss/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.concurrent/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.httpserver/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.naming/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.jvmstat/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jartool/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdwp.agent/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.le/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.ed/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.scripting/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.attach/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.auth/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.xml.dom/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.charsets/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.sctp/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.rmi/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.smartcardio/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jstatd/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.transaction.xa/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.hotspot.agent/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdi/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.javadoc/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jlink/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.nio.mapmode/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.jfr/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.accessibility/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.datatransfer/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jshell/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdeps/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.random/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.ec/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.agent/
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml.crypto/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.ci/
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.ci/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.ci/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.ci/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml.crypto/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml.crypto/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml.crypto/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml.crypto/santuario.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.agent/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.agent/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.agent/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.ec/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.ec/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.ec/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.random/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.random/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.random/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/freetype.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/mesa3d.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/colorimaging.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/libpng.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/xwd.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/giflib.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/harfbuzz.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/jpeg.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.desktop/lcms.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdeps/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdeps/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdeps/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jshell/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jshell/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jshell/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.datatransfer/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.datatransfer/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.datatransfer/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.accessibility/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.accessibility/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.accessibility/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.jfr/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.jfr/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management.jfr/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.nio.mapmode/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.nio.mapmode/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.nio.mapmode/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jlink/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jlink/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jlink/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.javadoc/jquery.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.javadoc/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.javadoc/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.javadoc/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.javadoc/jqueryUI.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdi/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdi/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdi/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.hotspot.agent/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.hotspot.agent/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.hotspot.agent/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.transaction.xa/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.transaction.xa/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.transaction.xa/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jstatd/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jstatd/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jstatd/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.smartcardio/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.smartcardio/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.smartcardio/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.smartcardio/pcsclite.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.rmi/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.rmi/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.rmi/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.sctp/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.sctp/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.sctp/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.charsets/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.charsets/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.charsets/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.xml.dom/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.xml.dom/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.xml.dom/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.auth/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.auth/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.auth/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.attach/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.attach/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.attach/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.scripting/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.scripting/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.scripting/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.ed/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.ed/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.ed/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.le/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.le/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.le/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.le/jline.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdwp.agent/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdwp.agent/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jdwp.agent/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jartool/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jartool/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jartool/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.jvmstat/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.jvmstat/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.jvmstat/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.naming/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.naming/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.naming/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.httpserver/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.httpserver/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.httpserver/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.concurrent/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.concurrent/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.concurrent/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.jgss/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.jgss/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.security.jgss/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql.rowset/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql.rowset/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.sql.rowset/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jconsole/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jconsole/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jconsole/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.opt/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.opt/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.opt/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.opt/jopt-simple.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jpackage/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jpackage/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jpackage/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.net.http/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.net.http/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.net.http/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/asm.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/zlib.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/public_suffix.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/cldr.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/icu.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/unicode.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/c-libutl.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.base/aes.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.management/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.logging/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.logging/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.logging/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.editpad/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.editpad/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.editpad/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.cryptoki/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.cryptoki/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.cryptoki/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.cryptoki/pkcs11wrapper.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.crypto.cryptoki/pkcs11cryptotoken.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.prefs/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.prefs/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.prefs/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.compiler/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.compiler/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.compiler/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.rmi/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.rmi/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.rmi/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.localedata/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.localedata/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.localedata/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.localedata/cldr.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.localedata/thaidict.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.instrument/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.instrument/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.instrument/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.dns/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.dns/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.naming.dns/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jcmd/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jcmd/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jcmd/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/bcel.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/xalan.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/dom.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/jcup.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.xml/xerces.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.compiler/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.compiler/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.compiler/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.dynalink/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.dynalink/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.dynalink/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.dynalink/dynalink.md
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.vector/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.vector/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.incubator.vector/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.zipfs/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.zipfs/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.zipfs/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jsobject/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jsobject/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jsobject/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.net/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.net/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.net/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.sasl/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.sasl/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.sasl/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jfr/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jfr/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.jfr/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.jgss/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.jgss/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.security.jgss/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.se/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.se/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.se/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler.management/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler.management/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.internal.vm.compiler.management/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported.desktop/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported.desktop/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/jdk.unsupported.desktop/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management.rmi/LICENSE
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management.rmi/ADDITIONAL_LICENSE_INFO
x ./jdk-20.0.1.jdk/Contents/Home/legal/java.management.rmi/ASSEMBLY_EXCEPTION
x ./jdk-20.0.1.jdk/Contents/Home/lib/libnet.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libnio.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libinstrument.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libzip.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/psfontj2d.properties
x ./jdk-20.0.1.jdk/Contents/Home/lib/fontconfig.properties.src
x ./jdk-20.0.1.jdk/Contents/Home/lib/libfreetype.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjli.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libsplashscreen.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libmanagement_ext.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libdt_socket.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libj2pkcs11.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/jvm.cfg
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjimage.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/security/
x ./jdk-20.0.1.jdk/Contents/Home/lib/jfr/
x ./jdk-20.0.1.jdk/Contents/Home/lib/shaders.metallib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libosxkrb5.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libosxui.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/tzdb.dat
x ./jdk-20.0.1.jdk/Contents/Home/lib/libmanagement_agent.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/librmi.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjdwp.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libawt_lwawt.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/server/
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjavajpeg.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libmlib_image.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libmanagement.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjsound.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/ct.sym
x ./jdk-20.0.1.jdk/Contents/Home/lib/libj2pcsc.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjsig.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libprefs.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libsyslookup.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjawt.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libattach.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/jrt-fs.jar
x ./jdk-20.0.1.jdk/Contents/Home/lib/libfontmanager.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/fontconfig.bfc
x ./jdk-20.0.1.jdk/Contents/Home/lib/src.zip
x ./jdk-20.0.1.jdk/Contents/Home/lib/jspawnhelper
x ./jdk-20.0.1.jdk/Contents/Home/lib/libosxsecurity.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libextnet.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjaas.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/liblcms.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libverify.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/psfont.properties.ja
x ./jdk-20.0.1.jdk/Contents/Home/lib/libj2gss.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libsaproc.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/modules
x ./jdk-20.0.1.jdk/Contents/Home/lib/classlist
x ./jdk-20.0.1.jdk/Contents/Home/lib/libjava.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libawt.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libosx.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/libosxapp.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/server/classes_nocoops.jsa
x ./jdk-20.0.1.jdk/Contents/Home/lib/server/libjvm.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/server/classes.jsa
x ./jdk-20.0.1.jdk/Contents/Home/lib/server/libjsig.dylib
x ./jdk-20.0.1.jdk/Contents/Home/lib/jfr/default.jfc
x ./jdk-20.0.1.jdk/Contents/Home/lib/jfr/profile.jfc
x ./jdk-20.0.1.jdk/Contents/Home/lib/security/public_suffix_list.dat
x ./jdk-20.0.1.jdk/Contents/Home/lib/security/default.policy
x ./jdk-20.0.1.jdk/Contents/Home/lib/security/cacerts
x ./jdk-20.0.1.jdk/Contents/Home/lib/security/blocked.certs
x ./jdk-20.0.1.jdk/Contents/Home/include/jawt.h
x ./jdk-20.0.1.jdk/Contents/Home/include/classfile_constants.h
x ./jdk-20.0.1.jdk/Contents/Home/include/jdwpTransport.h
x ./jdk-20.0.1.jdk/Contents/Home/include/jvmti.h
x ./jdk-20.0.1.jdk/Contents/Home/include/jni.h
x ./jdk-20.0.1.jdk/Contents/Home/include/jvmticmlr.h
x ./jdk-20.0.1.jdk/Contents/Home/include/darwin/
x ./jdk-20.0.1.jdk/Contents/Home/include/darwin/jni_md.h
x ./jdk-20.0.1.jdk/Contents/Home/include/darwin/jawt_md.h
x ./jdk-20.0.1.jdk/Contents/Home/bin/jwebserver
x ./jdk-20.0.1.jdk/Contents/Home/bin/jarsigner
x ./jdk-20.0.1.jdk/Contents/Home/bin/jfr
x ./jdk-20.0.1.jdk/Contents/Home/bin/jdb
x ./jdk-20.0.1.jdk/Contents/Home/bin/jstack
x ./jdk-20.0.1.jdk/Contents/Home/bin/rmiregistry
x ./jdk-20.0.1.jdk/Contents/Home/bin/jar
x ./jdk-20.0.1.jdk/Contents/Home/bin/jcmd
x ./jdk-20.0.1.jdk/Contents/Home/bin/jrunscript
x ./jdk-20.0.1.jdk/Contents/Home/bin/jps
x ./jdk-20.0.1.jdk/Contents/Home/bin/java
x ./jdk-20.0.1.jdk/Contents/Home/bin/jhsdb
x ./jdk-20.0.1.jdk/Contents/Home/bin/javap
x ./jdk-20.0.1.jdk/Contents/Home/bin/jdeprscan
x ./jdk-20.0.1.jdk/Contents/Home/bin/javac
x ./jdk-20.0.1.jdk/Contents/Home/bin/keytool
x ./jdk-20.0.1.jdk/Contents/Home/bin/jmod
x ./jdk-20.0.1.jdk/Contents/Home/bin/jmap
x ./jdk-20.0.1.jdk/Contents/Home/bin/jshell
x ./jdk-20.0.1.jdk/Contents/Home/bin/jstat
x ./jdk-20.0.1.jdk/Contents/Home/bin/jlink
x ./jdk-20.0.1.jdk/Contents/Home/bin/serialver
x ./jdk-20.0.1.jdk/Contents/Home/bin/javadoc
x ./jdk-20.0.1.jdk/Contents/Home/bin/jinfo
x ./jdk-20.0.1.jdk/Contents/Home/bin/jstatd
x ./jdk-20.0.1.jdk/Contents/Home/bin/jdeps
x ./jdk-20.0.1.jdk/Contents/Home/bin/jconsole
x ./jdk-20.0.1.jdk/Contents/Home/bin/jpackage
x ./jdk-20.0.1.jdk/Contents/Home/bin/jimage
x ./jdk-20.0.1.jdk/Contents/_CodeSignature/CodeResources
```

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption><p>Powershell output during unzip process</p></figcaption></figure>

#### Move the unzip folder to Progams Folder

```
[INPUT]
sudo mv jdk-20.0.1.jdk /Library/Java/JavaVirtualMachines

[OUTPUT]
---
```

#### Set environment variables

* [Java official documentation](https://dev.java/learn/getting-started/)

<!---->

* [ ] Set JAVA\_HOME variable

```
[INPUT]
jenv enable-plugin export

[OUTPUT]
echo $JAVA_HOME
/Users/yannmenoud/.jenv/versions/openjdk64-20.0.1
```

* [ ] Update PATH environment variable

{% hint style="info" %}
Backup your current path before updating it.

echo %PATH% > path.back
{% endhint %}

I use Jenv to handle my versions of Java. It changes automatilly the path.

```
[INPUT]


[OUTPUT]

```

* [ ] Check the variables settings

```
[INPUT]
echo $PATH

[OUTPUT]
/Users/yannmenoud/.jenv/shims:/Users/yannmenoud/.jenv/bin:/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/System/Cryptexes/App/usr/bin:/usr/bin:/bin:/usr/sbin:/sbin:/Library/Apple/usr/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/local/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/appleinternal/bin:/usr/local/bin:/Users/yannmenoud/development/flutter/bin:/Users/yannmenoud/Desktop/CPNV/MAW12/helpers/MatuXor-EDT-Extractors
```

## Build and test the project

```
[INPUT]
./mvnw spring-boot:run

[OUTPUT]


              |\      _,,,--,,_
             /,`.-'`'   ._  \-;;,_
  _______ __|,4-  ) )_   .;.(__`'-'__     ___ __    _ ___ _______
 |       | '---''(_/._)-'(_\_)   |   |   |   |  |  | |   |       |
 |    _  |    ___|_     _|       |   |   |   |   |_| |   |       | __ _ _
 |   |_| |   |___  |   | |       |   |   |   |       |   |       | \ \ \ \
 |    ___|    ___| |   | |      _|   |___|   |  _    |   |      _|  \ \ \ \
 |   |   |   |___  |   | |     |_|       |   | | |   |   |     |_    ) ) ) )
 |___|   |_______| |___| |_______|_______|___|_|  |__|___|_______|  / / / /
 ==================================================================/_/_/_/

:: Built with Spring Boot :: 3.0.4

```
