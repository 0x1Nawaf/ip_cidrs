# IPs (CIDR list)

::

## Usage

- Import into firewall/ACL tools that accept CIDR lists (pfSense, ipset, AWS tooling, cloud WAFs).

- ipset (Linux):

1. Create set: sudo ipset create ip`s hash:net

2. Add entries: while read ip; do sudo ipset add cidr $ip; done < ips.list

3. Apply in iptables: sudo iptables -I INPUT -m set --match-set saudi src -j DROP

- AWS (CLI): aws ec2 create-managed-prefix-list / aws ec2 modify-managed-prefix-list or use security group automation to import entries.

- pfSense: Use Aliases → Networks → Import, paste list, save and apply to rules.

- For scripts: treat each non-empty line as a CIDR; skip blank lines and comments

