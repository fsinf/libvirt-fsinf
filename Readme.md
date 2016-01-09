# libvirt-fsinf

This is a Debian (native) package installing various improvements to libvirt.

Currently this only installs some nwfilters:

Filter | Description
-------|------------
`allow-incoming-ipv6` | Allow incoming IPv6 traffic.
`no-dhcpv6-server` | Filter DHCP6 traffic.
`no-ipv6-spoofing` | Drop IPv6 traffic with any source address not configured by the `IPV6` parameter.
`no-ipv6-router-advertisement` | Filter IPv6 router advertisement traffic.
`clean-traffic-fsinf` | Improved version of the stock `clean-traffic` filter using all of the above filters.

To use the `clean-traffic-fsinf` filter, add this to your interface config:

```
<interface type='bridge'>
    <!-- ... your other interface config -->
    <mac address='01:23:45:67:89:ab'/>
    <filterref filter='clean-traffic-fsinf'>
        <parameter name='IP' value='93.184.216.34'/>
        <parameter name='IPV6' value='2606:2800:220:1:248:1893:25c8:1946'/>
        <parameter name='MAC' value='01:23:45:67:89:ab'/>
    </filterref>
</interface>
```
