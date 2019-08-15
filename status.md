# Node status API:

## Events:


### All events:
curl -X GET 'https://master.inf.puppet.vm:8081/pdb/query/v4/events' \
  --tlsv1 \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  --cert /etc/puppetlabs/puppet/ssl/certs/simon.anderson-awskit-linux-1.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/simon.anderson-awskit-linux-1.pem | jq


### Output:

{
  "new_value": "",
  "report": "00b7da9ed2332741293d0fd876551aa490133091",
  "corrective_change": false,
  "run_start_time": "2019-08-15T00:22:23.552Z",
  "property": null,
  "file": "/opt/puppetlabs/puppet/modules/puppet_enterprise/manifests/trapperkeeper/pe_service.pp",
  "old_value": "",
  "containing_class": "Puppet_enterprise::Master::Puppetserver",
  "line": 10,
  "resource_type": "Service",
  "status": "success",
  "configuration_version": "aa961251e02f0e7726589882944f7a4c13643680",
  "resource_title": "pe-puppetserver",
  "environment": "production",
  "timestamp": "2019-08-15T00:23:33.126Z",
  "run_end_time": "2019-08-15T00:23:37.975Z",
  "report_receive_time": "2019-08-15T00:23:39.851Z",
  "containment_path": [
    "Stage[main]",
    "Puppet_enterprise::Master::Puppetserver",
    "Puppet_enterprise::Trapperkeeper::Pe_service[puppetserver]",
    "Service[pe-puppetserver]"
  ],
  "certname": "master.inf.puppet.vm",
  "message": "Triggered 'refresh' from 2 events"
}


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
