# Configuration drift

# Pre-requisite:
Add the certificate to the file:

`/etc/puppetlabs/puppetdb/certificate-whitelist `


### List nodes:
curl 'https://master.inf.puppet.vm:8081/pdb/query/v4/nodes' \
  --tlsv1 \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem

### Status call:
curl 'https://master.inf.puppet.vm:4433/status/v1/services' \
  --tlsv1 \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem





## With no-op enabled:

### API call:

## Without no-op enabled:

### API remediation:
