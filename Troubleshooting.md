# 1. Jira plugin project:

When execute command `atlas-mvn package` at plugin project

https://community.atlassian.com/t5/Jira-Questions/Unknown-lifecycle-phase-error/qaq-p/1006922

**Problem**:
`C:\Users\Legion\myPlugin>atlas-mvn package`

[INFO] Project POM found
"else" no se reconoce como un comando interno o externo,
programa o archivo por lotes ejecutable.
Executing: "C:\Applications\Atlassian\atlassian-plugin-sdk-8.0.16\apache-maven-3.5.4\bin\mvn.cmd" ${mavenPluginName}=$mavenPluginName -gs C:\Applications\Atlassian\atlassian-plugin-sdk-8.0.16\apache-maven-3.5.4/conf/settings.xml package
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------< com.atlassian.tutorial:myPlugin >-------------------
[INFO] Building myPlugin 1.0.0-SNAPSHOT
[INFO] --------------------------[ atlassian-plugin ]--------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 1.378 s
[INFO] Finished at: 2020-07-02T13:27:42+05:30
[INFO] ------------------------------------------------------------------------
[ERROR] Unknown lifecycle phase "${mavenPluginName}=$mavenPluginName". You must specify a valid lifecycle phase or a goal in the format <plugin-prefix>:<goal> or <plugin-group-id>:<plugin-artifact-id>[:<plugin-version>]:<goal>. Available lifecycle phases are: validate, initialize, generate-sources, process-sources, generate-resources, process-resources, compile, process-classes, generate-test-sources, process-test-sources, generate-test-resources, process-test-resources, test-compile, process-test-classes, test, prepare-package, package, pre-integration-test, integration-test, post-integration-test, verify, install, deploy, pre-clean, clean, post-clean, pre-site, site, post-site, site-deploy. -> [Help 1]
[ERROR]
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/LifecyclePhaseNotFoundException



**Solution**:
Looks like I was able to fix "Lifecycle Phase" error as follows (I got it on Windows):

1. In "atlas-mvn.bat" file comment out the following line:
`call set MVN_COMMAND=%%MVN_COMMAND:${mavenPluginName}=%MVN_PLUGIN%%%`

2. Replace it with:
`call set MVN_COMMAND=%%MVN_COMMAND:%%`

# 2. Hyper-V Docker
 The issue stared when Hyper-v has been stopped by user using powershell command and control panel.
 
**Problem**:
Activate hyper-v on windows 10 Pro. 
When windows starts it says that docker is not running
`Docker for Windows error: “Hardware assisted virtualization and data execution protection must be enabled in the BIOS”`

**Solution**:
https://stackoverflow.com/questions/39684974/docker-for-windows-error-hardware-assisted-virtualization-and-data-execution-p

Enable Hypervisor with:
`bcdedit /set hypervisorlaunchtype auto` 


