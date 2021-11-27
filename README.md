# k8s-node-bootstrap-helm-chart
An inofficial Helm chart for GCP's tutorial on "Automatically bootstrapping GKE nodes with DaemonSets".

For the original, official tutorial material, please see these links:
- https://cloud.google.com/solutions/automatically-bootstrapping-gke-nodes-with-daemonsets
- https://github.com/GoogleCloudPlatform/solutions-gke-init-daemonsets-tutorial

## DISCLAIMER

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

https://github.com/michiwerner/k8s-node-bootstrap-helm-chart/blob/main/LICENSE

## Installation

Using Helm 3.x, the installation is a two-step process.

First, add the repository:

<pre><code>helm repo add k8s-node-bootstrap https://michiwerner.github.io/k8s-node-bootstrap-helm-chart/releases</code></pre>

Then, install the chart:

<pre><code>helm install -n kube-system node-bootstrap k8s-node-bootstrap/node-bootstrap</code></pre>

It is possible to deploy more than one instance (release) of this chart. This might be useful if you want to bootstrap
different node types with different entrypoint scripts, e.g. using node selectors. All Kubernetes resources incorporate
the helm release name into their own names to avoid collisions.

## Usage

For now, please refer to the values.yaml for a list of available settings. You definitely want to set the *entrypointScript* value
because it is the very script which is run to bootstrap the node(s).

For an example of a complex bootstrap script, please refer to: https://github.com/GoogleCloudPlatform/solutions-gke-init-daemonsets-tutorial/blob/master/cm-entrypoint.yaml