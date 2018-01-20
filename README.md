# What

This repo will be useful to you if you have [Ubiquiti Networks
UniFi](https://unifi-sdn.ubnt.com/) devices and you use
[Prometheus](https://prometheus.io/) for your metrics.


# Scraping metrics from UniFi devices

The included `snmp.yml` is ready to go as is.  Simply get the [SNMP
exporter](https://github.com/prometheus/snmp_exporter), start it and you
should be able to get metrics from your UniFi device.

Test with curl(1):
```
curl -s 'localhost:9116/snmp?target=X.X.X.X&module=unifi'
```

Now you can configure Prometheus to scrape this endpoint and you're
done.

# Customising what metrics are scraped

The included `generator.yml` can be updated to scrape any additional
metrics you need.

To use the generator, you'll need to get the Ubiquiti Networks MIBs from
here: http://dl.ubnt-ut.com/snmp/UBNT-MIB and
http://dl.ubnt-ut.com/snmp/UBNT-UniFi-MIB and place them into
`$HOME/.snmp/mibs`.

The generator
[docs](https://github.com/prometheus/snmp_exporter/tree/master/generator)
should have all you need.

# External links

[Prometheus SNMP exporter](https://github.com/prometheus/snmp_exporter)
has a great README.  Make sure you read it thoroughly, as SNMP and MIBs
can be confusing.

The [using and loading
MIBs](http://net-snmp.sourceforge.net/wiki/index.php/TUT:Using_and_loading_MIBS)
section of the official Net-SNMP documentation is great as well.
