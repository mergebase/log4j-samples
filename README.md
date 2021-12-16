
# log4j-samples
Samples of log4j library versions to help log4j scanners / detectors (including ours: [log4j-detector](https://github.com/mergebase/log4j-detector)) improve their accuracy.

The samples include shaded jars, [uber jars](https://mergebase.com/blog/software-composition-analysis-sca-vs-java-uber-jars/), spring-boot executable jars, jars inside jars, exploded jars, etc.

# Directory Organization

- [./false-hits/](./false-hits/) - No sample in here is vulnerable to CVE-2021-45046 or CVE-2021-44228.
- [./old-hits/](./old-hits/) - Every sample in here contains versions of Log4J (1.x and 2.x) that are too old to be vulnerable to CVE-2021-45046 or CVE-2021-44228.
- [./true-hits/](./true-hits/) - Every sample in here **is vulnerable** to CVE-2021-45046 and CVE-2021-44228.

# Why Are \*.zip Files Included In The Samples?

Java treats \*.zip exactly the same as \*.jar, and always has. You really don't want attackers to simmply rename "webapp/WEB-INF/lib/log4j-core-2.9.jar" to "log4j-core-2.9.zip" to defeat your scanner! Don't believe me?  Try this:

```
$ wget https://github.com/mergebase/log4j-samples/raw/master/false-hits/log4j-detector-2021.12.16.zip
$ java -jar log4j-detector-2021.12.16.zip

Usage: java -jar log4j-detector-2021.12.16.jar [--verbose] [paths to scan...]

Exit codes:  0 = No vulnerable Log4J versions found.
             1 = At least one legacy Log4J 1.x version found.
             2 = At least one vulnerable Log4J 2.x version found.

About - MergeBase log4j detector (version 2021.12.16)
Docs  - https://github.com/mergebase/log4j-detector 
(C) Copyright 2021 Mergebase Software Inc. Licensed to you via GPLv3.
```
(Similarly, this also works: `java -cp log4j-detector-2021.12.16.zip com.mergebase.log4j.Log4JDetector`).


# Latest Scan With [log4j-detector](https://github.com/mergebase/log4j-detector)

```
-- github.com/mergebase/log4j-detector v2021.12.16 (by mergebase.com) analyzing paths (could take a while).
-- Note: specify the '--verbose' flag to have every file examined printed to STDERR.
/opt/mergebase/log4j-samples/false-hits/exploded/2.12.2/org/apache/logging/log4j contains Log4J-2.x   >= 2.12.2 _SAFE_ :-)
/opt/mergebase/log4j-samples/false-hits/log4j-core-2.12.2.jar contains Log4J-2.x   >= 2.12.2 _SAFE_ :-)
/opt/mergebase/log4j-samples/false-hits/log4j-core-2.16.0.jar contains Log4J-2.x   >= 2.16.0 _SAFE_ :-)
/opt/mergebase/log4j-samples/old-hits/log4j-1.1.3.jar contains Log4J-1.x   <= 1.2.17 _OLD_ :-|
/opt/mergebase/log4j-samples/old-hits/log4j-1.2.17.jar contains Log4J-1.x   <= 1.2.17 _OLD_ :-|
/opt/mergebase/log4j-samples/old-hits/log4j-core-2.0-beta2.jar contains Log4J-2.x   <= 2.0-beta8 _POTENTIALLY_SAFE_ :-| (or did you already remove JndiLookup.class?) 
/opt/mergebase/log4j-samples/true-hits/exploded/2.12.1/org/apache/logging/log4j contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.0-beta9.jar contains Log4J-2.x   >= 2.0-beta9 (< 2.10.0) _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.10.0.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.10.0.zip contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.15.0.jar contains Log4J-2.x   >= 2.15.0 _OKAY_ :-|
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.9.1.jar contains Log4J-2.x   >= 2.0-beta9 (< 2.10.0) _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/shaded/clt-1.0-SNAPSHOT.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/springboot-executable/spiff-0.0.1-SNAPSHOT.ear!/WEB-INF/lib/log4j-core-2.10.0.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/springboot-executable/spiff-0.0.1-SNAPSHOT.jar!/WEB-INF/lib/log4j-core-2.10.0.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/springboot-executable/spiff-0.0.1-SNAPSHOT.war!/WEB-INF/lib/log4j-core-2.10.0.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/springboot-executable/spiff-0.0.1-SNAPSHOT.zip!/WEB-INF/lib/log4j-core-2.10.0.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/uber/infinispan-embedded-query-8.2.12.Final.jar contains Log4J-2.x   >= 2.0-beta9 (< 2.10.0) _VULNERABLE_ :-(
```

