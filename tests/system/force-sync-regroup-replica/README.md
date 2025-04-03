# Test ForceRegroupReplicaBeforePrimaryFailover Configuration

This test verifies the behavior of the `ForceRegroupReplicaBeforePrimaryFailover` configuration option during a master failover operation.

## Purpose

When `ForceRegroupReplicaBeforePrimaryFailover` is set to `true`, Orchestrator will ensure that replicas are regrouped synchronously during master failover, even when the chosen candidate replica is considered ideal. This improves consistency by ensuring all replicas are properly positioned in the topology before completing the failover, at the cost of potentially longer failover time.

## Test Flow

1. Set the `ForceRegroupReplicaBeforePrimaryFailover` configuration option to `true`
2. Force a master failover operation
3. Verify in the logs that replication regrouping occurred synchronously and was not postponed 
4. Verify that the new topology has all replicas properly positioned under the new master

This test demonstrates how Orchestrator can be configured to prioritize complete topology consistency over faster failover times in scenarios where ensuring proper replica positioning is critical.
