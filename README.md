
# log4j-samples
Samples of log4j library versions to help log4j scanners / detectors (including ours: [github.com/mergebase/log4j-detector](https://github.com/mergebase/log4j-detector)) improve their accuracy.

Includes shaded jars, uber jars, spring-boot executable jars, jars inside jars, etc.

# Latest Scan

```
-- github.com/mergebase/log4j-detector v2021.12.16 (by mergebase.com) analyzing paths (could take a while).
-- Note: specify the '--verbose' flag to have every file examined printed to STDERR.
/opt/mergebase/log4j-samples/false-hits/exploded/2.12.2/org/apache/logging/log4j contains Log4J-2.x   >= 2.12.2 _SAFE_ :-)
/opt/mergebase/log4j-samples/false-hits/log4j-core-2.16.0.jar contains Log4J-2.x   >= 2.16.0 _SAFE_ :-)
/opt/mergebase/log4j-samples/false-hits/log4j-over-slf4j-1.7.32.jar contains Log4J-1.x   <= 1.2.17 _OLD_ :-|
/opt/mergebase/log4j-samples/old-hits/log4j-1.1.3.jar contains Log4J-1.x   <= 1.2.17 _OLD_ :-|
/opt/mergebase/log4j-samples/old-hits/log4j-1.2.17.jar contains Log4J-1.x   <= 1.2.17 _OLD_ :-|
/opt/mergebase/log4j-samples/old-hits/log4j-core-2.0-beta2.jar contains Log4J-2.x   <= 2.0-beta8 _POTENTIALLY_SAFE_ :-| (or did you already remove JndiLookup.class?) 
/opt/mergebase/log4j-samples/true-hits/exploded/2.12.1/org/apache/logging/log4j contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.0-beta9.jar contains Log4J-2.x   >= 2.0-beta9 (< 2.10.0) _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.10.0.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.15.0.jar contains Log4J-2.x   >= 2.15.0 _OKAY_ :-|
/opt/mergebase/log4j-samples/true-hits/log4j-core-2.9.1.jar contains Log4J-2.x   >= 2.0-beta9 (< 2.10.0) _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/shaded/clt-1.0-SNAPSHOT.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/springboot-executable/spiff-0.0.1-SNAPSHOT.war!/WEB-INF/lib/log4j-core-2.10.0.jar contains Log4J-2.x   >= 2.10.0 _VULNERABLE_ :-(
/opt/mergebase/log4j-samples/true-hits/springboot-executable/spiff-0.0.1-SNAPSHOT.war!/WEB-INF/lib/log4j-over-slf4j-1.7.25.jar contains Log4J-1.x   <= 1.2.17 _OLD_ :-|
/opt/mergebase/log4j-samples/true-hits/uber/infinispan-embedded-query-8.2.12.Final.jar contains Log4J-2.x   >= 2.0-beta9 (< 2.10.0) _VULNERABLE_ :-(
```

Notice our latest scan has two mistakes (see log4j-detector [issue #36](https://github.com/mergebase/log4j-detector/issues/36)):  "log4j-over-slf4j-1.7.32.jar" and "log4j-over-slf4j-1.7.25.jar" are not actually Log4J-1.x.
