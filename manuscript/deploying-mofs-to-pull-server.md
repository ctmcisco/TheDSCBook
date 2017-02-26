# Deploying MOFs to a Pull Server
Once you've created a MOF, you can obviously deploy it in Push mode by running `Start-DscConfiguration` - we've covered that. But you may also wish to deploy it to either an HTTP(S) or an SMB Pull server. That's straightforward: when you configured your pull server, you specified the folder in which configurations would live (see, "Setting Up a Pull Server" in this book). Simply copy the configuration MOF files to that location. You'll also need to create a checksum file for each MOF; the `New-DscChecksum` command can do that for you. 

MOF naming depends on how you've configured your LCMs. If you're using ConfigurationIds (which is the the only option in v4), then each MOF needs to have the GUID - that is, the Configuration ID - that you've assigned the node (or nodes) that will pull the configuration. Checksum files have the same filename, with the addition of a ".mof.checksum" filename extension. However, if you're using Configuration Names in v5 or later, then MOF filenames take the configurations' names - like "Bob.mof," with "Bob.mof.checksum" being the checksum.