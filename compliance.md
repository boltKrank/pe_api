# Compliance API example:

## Check status of all nodes for CIS fact:

curl -X GET 'https://master.inf.puppet.vm:8081/pdb/query/v4/facts' \
  --data-urlencode 'query=["~", "name", "cis"]' \
  --tlsv1 \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem | jq
