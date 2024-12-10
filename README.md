# FiaB-Updates
A place to announce updates, security alerts, and patches to the FAIR-in-a-Box modules

# NEW!!  FAIR-in-a-Box Security Upgrades

With the arrival of ERDERA, we have improved the way we handle security upgrades on all FiaB components.  The basic workflow is:

```
start the base image
open a shell into that base container
apt-get dist-upgrade   OR   apk upgrade
commit the patched image
upload the patched, timestamped image to the FAIR Data Systems GitHub
run Trivy to do a security audit on the patched version
write the trivy logs to a folder (in the FiaB installer folder) with the same timestamp, that you can access and determine the severity of any remaining security holes
close the container
git commit the patched installer file and the new logs
```




# FAIR-in-a-Box

FiaB is a suite of Docker images, and an installer/bootstrapper, that results in an end-to-end pipeline for FAIRification of legacy clinical data, publishing of that data and its associated metadata,privacy-preserving query and exploration of data and metadata, and user management. The European Joint Programme on Rare Disease has defined three "levels" of access to data/metadata.  L1 is access to metadata only, and is the minimal requried to be FAIR.  L2 is discovery of resources based on data-level queries, but with only returning anonymous counts or yes/no.  L3 is data-level query for the purpose of analytics, but without exposing patient-specific data.

The primary components of FAIR in a Box are

<table><tr><td>Function</td><td>Provided by</td><td>Source</td><td>License</td><td>Required/Optional</td></tr>

<tr>
<td>Installer</td>
<td>Bash script</td>
<td>run_me_to_install.sh</td>
<td>Open Source</td>
<td>Required L1</td>
</tr>

<tr>
<td>Authentication management</td>
<td>MongoDB</td>
<td>Mongodb 7.0 Docker image (mongo:7.0)</td>
<td>******</td>
<td>Required L1</td>
</tr>

<tr>
<td>Metadata Server</td>
<td>FAIR Data Point</td>
<td>fairdata/fairdatapoint:1.16.2 Docker image</td>
<td>Open source</td>
<td>Required L1</td>
</tr>


<tr>
<td>Metadata Client</td>
<td>FAIR Data Point Client</td>
<td>fairdata/fairdatapoint-client:1.16.3 Docker image</td>
<td>Open source</td>
<td>Required L1</td>
</tr>


<tr>
<td>Metadata and data storage</td>
<td>GraphDB</td>
<td>ontotext/graphdb:10.7.3</td>
<td>Commercial, free-for-limited-use</td>
<td>Required L1</td>
</tr>


<tr>
<td>Transformation trigger</td>
<td>CDE-Box_Daemon</td>
<td>markw/cde-box-daemon:0.5.4  Docker image</td>
<td>Open source</td>
<td>Optional; Required L2</td>
</tr>


<tr>
<td>Pre-transformation quality control</td>
<td>CARE-SM Toolkit</td>
<td>pabloalarconm/care-sm-toolkit:0.1.6</td>
<td>Open source</td>
<td>Optional; Required L2</td>
</tr>

<tr>
<td>Transformation</td>
<td>YARRRML-RML from RML.io</td>
<td>markw/yarrrml-rml-ejp:0.1.1 Docker image</td>
<td>Open source</td>
<td>Optional; Required L2</td>
</tr>


<tr>
<td>Privacy-preserving data-level discoveryn</td>
<td>Beacon2 from GA4GH Project</td>
<td>pabloalarconm/beacon-api4care-sm:0.2.2 Docker image</td>
<td>Open source</td>
<td>Optional; Required L2</td>
</tr>


<tr>
<td>Privacy-preserving analytical query</td>
<td>Shallot</td>
<td>markw/shallot:0.0.2 Docker image</td>
<td>Open source</td>
<td>Optional; Required L3</td>
</tr>


