# Node status API:

## Events:


### All events:
curl -X GET 'https://master.inf.puppet.vm:8081/pdb/query/v4/events' \
  --tlsv1 \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem | jq

### All corrective change events:
  curl -X GET 'https://master.inf.puppet.vm:8081/pdb/query/v4/events' \
    --data-urlencode 'query=["=", "corrective_change", true]' \
    --tlsv1 \
    --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
    --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
    --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem | jq

### All intentional change events:
curl -X GET 'https://master.inf.puppet.vm:8081/pdb/query/v4/events' \
        --data-urlencode 'query=["=", "corrective_change", false]' \
        --tlsv1 \
        --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
        --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
        --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem | jq

### TODO: All intentional change events (non-master):
curl -X GET 'https://master.inf.puppet.vm:8081/pdb/query/v4/events' \
        --data-urlencode 'query=["!=", "certname", "master.inf.puppet.vm"]' \
        --tlsv1 \
        --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
        --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
        --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem | jq '.[] | select(.certname != "master.inf.puppet.vm")'


## HTTP API:

curl -X GET 'https://master.inf.puppet.vm:8081/pdb/query/v4/facts' \
  --data-urlencode 'query=["~", "name", "cis"]' \
  --tlsv1 \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem
