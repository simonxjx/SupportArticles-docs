---
title: Troubleshoot the ZonalAllocationFailed, AllocationFailed, or OverconstrainedAllocationRequest error code
description: Troubleshoot the ZonalAllocationFailed, AllocationFailed, or OverconstrainedAllocationRequest error when you create, deploy, or update a Kubernetes cluster.
ms.date: 04/22/2024
author: axelgMS
ms.author: axelg
editor: v-jsitser
ms.reviewer: rissing, chiragpa, erbookbi, v-leedennis, v-weizhu
ms.service: azure-kubernetes-service
ms.custom: sap:Create, Upgrade, Scale and Delete operations (cluster or nodepool)
---
# Troubleshoot the ZonalAllocationFailed, AllocationFailed, or OverconstrainedAllocationRequest error code

This article describes how to identify and resolve the `ZonalAllocationFailed`, `AllocationFailed`, or `OverconstrainedAllocationRequest` error that might occur when you try to create, deploy, or update a Microsoft Azure Kubernetes Service (AKS) cluster.

## Prerequisites

- [Azure CLI](/cli/azure/install-azure-cli) (optional), version 2.0.59 or a later version. If Azure CLI is already installed, you can find the version number by using `az --version`.

- [Azure PowerShell](/powershell/azure/install-az-ps) (optional).

## Symptoms

When you try to create an AKS cluster, you receive the following error message:

> Reconcile vmss agent pool error: VMSSAgentPoolReconciler retry failed:
>
> Category: InternalError;
>
> SubCode: ZonalAllocationFailed;
>
> Dependency: Microsoft.Compute/VirtualMachineScaleSet;
>
> OrginalError: Code="ZonalAllocationFailed"
>
> Message="**Allocation failed. We do not have sufficient capacity for the requested VM size in this zone.** Read more about improving likelihood of allocation success at <https://aka.ms/allocation-guidance>";
>
> AKSTeam: NodeProvisioning

Or, when you try to upgrade or scale up a cluster, you receive the following error message:

> Code="OverconstrainedAllocationRequest"
>
> Message="**Allocation failed. VM(s) with the following constraints cannot be allocated, because the condition is too restrictive.** Please remove some constraints and try again."

Or, when you use dedicated hosts in a cluster and try to create or scale up a node pool, you receive the following error message:

> Code="AllocationFailed"
>
> Message="**Allocation failed. VM allocation to the dedicated host failed. Please ensure that the dedicated host has enough capacity or try allocating elsewhere.**"

## Cause 1: Limited zone availability in a SKU

You're trying to deploy a cluster in a zone that has limited availability for the specific SKU.

## Solution 1: Use a different SKU, zone, or region

Try one or more of the following methods:

- Redeploy the cluster in the same region by using a different SKU.
- Redeploy the cluster in a different zone in that region.
- Redeploy the cluster in a different region.
- Create a new node pool in a different region or zone.

For more information about how to fix this error, see [Resolve errors for SKU not available](/azure/azure-resource-manager/troubleshooting/error-sku-not-available).

## Cause 2: Too many constraints for a virtual machine to accommodate

If you receive an `OverconstrainedAllocationRequest` error code, the Azure Compute platform can't allocate a new virtual machine (VM) to accommodate the required constraints. These constraints usually (but not always) include the following items:

- VM size
- VM SKU
- Accelerated networking
- Availability zone
- Ephemeral disk
- Proximity placement group (PPG)

## Solution 2: Don't associate a proximity placement group with the node pool

If you receive an `OverconstrainedAllocationRequest` error code, you can try to create a new node pool that isn't associated with a proximity placement group.

## Cause 3: Not enough dedicated hosts or fault domains

You're trying to deploy a node pool in a dedicated host group that has limited capacity or doesn't satisfy the fault domain constraint.

## Solution 3: Ensure you have enough dedicated hosts for your AKS nodes/VMSS

As per [Planning for ADH Capacity on AKS](/azure/aks/use-azure-dedicated-hosts#planning-for-adh-capacity-on-aks), you're responsible for planning enough dedicated hosts to span as many fault domains as required by your AKS VMSS. For example, if the AKS VMSS is created with *FaultDomainCount=2*, you need at least two dedicated hosts in different fault domains (*FaultDomain 0* and *FaultDomain 1*).

## More information

- [General troubleshooting of AKS cluster creation issues](troubleshoot-aks-cluster-creation-issues.md)

- [Virtual Machine Scale Sets - What to expect when using proximity placement groups](/azure/virtual-machine-scale-sets/proximity-placement-groups#what-to-expect-when-using-proximity-placement-groups)

- [Fix an AllocationFailed or ZonalAllocationFailed error when you create, restart, or resize Virtual Machine Scale Sets in Azure](../../virtual-machine-scale-sets/allocationfailed-or-zonalallocationfailed.md)

[!INCLUDE [Azure Help Support](../../../includes/azure-help-support.md)]
