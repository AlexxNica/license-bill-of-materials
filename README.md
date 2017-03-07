# What is it?

`license-bill-of-materials` uses `go list` tool over a Go workspace to collect the dependencies
of a package or command, detect their license if any and match them against
well-known templates.

The output record format follows the JSON representation of the go struct:

```go
type projectAndLicense struct {
	Project    string  `json:"project"`
	License    string  `json:"license,omitempty"`
	Confidence float64 `json:"confidence"`
	Error      string  `json:"error,omitempty"`
}
```

The output might have three array of records:

- Matched/Guessed license projects
- Error projects

Example output of Kubernetes API server:

```bash
$ license-bill-of-materials k8s.io/kubernetes/cmd/kube-apiserver
```

```json
[
	{
		"project": "k8s.io/kubernetes",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "cloud.google.com/go",
		"license": "Apache License 2.0",
		"confidence": 0.999
	},
	{
		"project": "github.com/Azure/azure-sdk-for-go",
		"license": "Apache License 2.0",
		"confidence": 0.999
	},
	{
		"project": "github.com/Azure/go-autorest/autorest",
		"license": "Apache License 2.0",
		"confidence": 0.968
	},
	{
		"project": "github.com/PuerkitoBio/purell",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.992
	},
	{
		"project": "github.com/PuerkitoBio/urlesc",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "github.com/aws/aws-sdk-go",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/beorn7/perks/quantile",
		"license": "MIT License",
		"confidence": 0.989
	},
	{
		"project": "github.com/coreos/etcd",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/coreos/go-oidc",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/coreos/go-systemd",
		"license": "Apache License 2.0",
		"confidence": 0.997
	},
	{
		"project": "github.com/coreos/pkg",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/davecgh/go-spew/spew",
		"license": "ISC License",
		"confidence": 1
	},
	{
		"project": "github.com/dgrijalva/jwt-go",
		"license": "MIT License",
		"confidence": 0.989
	},
	{
		"project": "github.com/docker/distribution",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/docker/engine-api/types",
		"license": "Apache License 2.0",
		"confidence": 0.966
	},
	{
		"project": "github.com/docker/go-connections/nat",
		"license": "Apache License 2.0",
		"confidence": 0.966
	},
	{
		"project": "github.com/docker/go-units",
		"license": "Apache License 2.0",
		"confidence": 0.966
	},
	{
		"project": "github.com/elazarl/go-bindata-assetfs",
		"license": "BSD 2-clause \"Simplified\" License",
		"confidence": 1
	},
	{
		"project": "github.com/emicklei/go-restful",
		"license": "MIT License",
		"confidence": 1
	},
	{
		"project": "github.com/evanphx/json-patch",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.979
	},
	{
		"project": "github.com/exponent-io/jsonpath",
		"license": "MIT License",
		"confidence": 1
	},
	{
		"project": "github.com/ghodss/yaml",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.836
	},
	{
		"project": "github.com/go-ini/ini",
		"license": "Apache License 2.0",
		"confidence": 0.997
	},
	{
		"project": "github.com/go-openapi/jsonpointer",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/go-openapi/jsonreference",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/go-openapi/spec",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/go-openapi/swag",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/gogo/protobuf",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.891
	},
	{
		"project": "github.com/golang/glog",
		"license": "Apache License 2.0",
		"confidence": 0.997
	},
	{
		"project": "github.com/golang/groupcache/lru",
		"license": "Apache License 2.0",
		"confidence": 0.997
	},
	{
		"project": "github.com/golang/protobuf",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.92
	},
	{
		"project": "github.com/google/gofuzz",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/gophercloud/gophercloud",
		"license": "Apache License 2.0",
		"confidence": 0.968
	},
	{
		"project": "github.com/grpc-ecosystem/grpc-gateway",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.979
	},
	{
		"project": "github.com/hashicorp/golang-lru/simplelru",
		"license": "Mozilla Public License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/hawkular/hawkular-client-go/metrics",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/howeyc/gopass",
		"license": "ISC License",
		"confidence": 0.985
	},
	{
		"project": "github.com/imdario/mergo",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "github.com/influxdata/influxdb",
		"license": "MIT License",
		"confidence": 1
	},
	{
		"project": "github.com/jmespath/go-jmespath",
		"license": "The Unlicense",
		"confidence": 0.353
	},
	{
		"project": "github.com/jonboulle/clockwork",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/juju/ratelimit",
		"license": "GNU Lesser General Public License v3.0",
		"confidence": 0.941
	},
	{
		"project": "github.com/mailru/easyjson",
		"license": "MIT License",
		"confidence": 0.989
	},
	{
		"project": "github.com/matttproud/golang_protobuf_extensions/pbutil",
		"license": "Apache License 2.0",
		"confidence": 0.999
	},
	{
		"project": "github.com/mesos/mesos-go",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/mitchellh/mapstructure",
		"license": "MIT License",
		"confidence": 1
	},
	{
		"project": "github.com/mxk/go-flowrate/flowrate",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.971
	},
	{
		"project": "github.com/pborman/uuid",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "github.com/pkg/errors",
		"license": "BSD 2-clause \"Simplified\" License",
		"confidence": 1
	},
	{
		"project": "github.com/prometheus/client_golang/prometheus",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/prometheus/client_model/go",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/prometheus/common",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/prometheus/procfs",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/rackspace/gophercloud",
		"license": "Apache License 2.0",
		"confidence": 0.968
	},
	{
		"project": "github.com/robfig/cron",
		"license": "MIT License",
		"confidence": 0.995
	},
	{
		"project": "github.com/rubiojr/go-vhd/vhd",
		"license": "MIT License",
		"confidence": 1
	},
	{
		"project": "github.com/samuel/go-zookeeper/zk",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.992
	},
	{
		"project": "github.com/spf13/cobra",
		"license": "Apache License 2.0",
		"confidence": 0.957
	},
	{
		"project": "github.com/spf13/pflag",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "github.com/ugorji/go/codec",
		"license": "MIT License",
		"confidence": 0.995
	},
	{
		"project": "github.com/vmware/govmomi",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/vmware/govmomi/vim25/xml",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "github.com/vmware/photon-controller-go-sdk/photon/lightwave",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "github.com/xanzy/go-cloudstack/cloudstack",
		"license": "Apache License 2.0",
		"confidence": 1
	},
	{
		"project": "golang.org/x/crypto",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "golang.org/x/net",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "golang.org/x/oauth2",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "golang.org/x/text",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "google.golang.org/api",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.966
	},
	{
		"project": "google.golang.org/api/googleapi/internal/uritemplates",
		"license": "MIT License",
		"confidence": 0.989
	},
	{
		"project": "google.golang.org/grpc",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.979
	},
	{
		"project": "gopkg.in/gcfg.v1",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.975
	},
	{
		"project": "gopkg.in/inf.v0",
		"license": "BSD 3-clause \"New\" or \"Revised\" License",
		"confidence": 0.975
	},
	{
		"project": "gopkg.in/natefinch/lumberjack.v2",
		"license": "MIT License",
		"confidence": 1
	},
	{
		"project": "gopkg.in/yaml.v2",
		"license": "GNU Lesser General Public License v3.0",
		"confidence": 0.953
	},
	{
		"project": "k8s.io/client-go",
		"license": "Apache License 2.0",
		"confidence": 1
	}
]
```

# Where does it come from?

Both the code and reference data were directly ported from:

  [https://github.com/benbalter/licensee](https://github.com/benbalter/licensee)
