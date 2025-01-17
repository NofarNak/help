# Access Roles and Permissions - Read-Only

As mentioned on the [Azure Tutorial](eco/azure-tutorials/) there is a three step process to set up  Eco Azure. The information on this page is relevant to Analysis step (Step 1).

## Azure Role needed for Eco Azure Analysis and Planning

The roles and billing access below is relevant only for customers who have not yet signed a contract for Eco Azure.

### Cost Management Reader

The Eco team requests the [Cost Management Reader role](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#cost-management-reader) to be applied to the user group of guest users for the Management Group OR Subscriptions scope that is going to be analyzed. The data is used to complete the initial analysis.

### Reservation Reader role

The Eco team requests customers to assign the [Azure Reservation Reader](https://docs.microsoft.com/en-us/azure/cost-management-billing/reservations/view-reservations#assign-a-reservation-reader-role-at-the-tenant-level) role to the user group of guest users in order to accurately perform the initial analysis.

### EA Read Only Admin (Applies to Enterprise Agreement only)

The Eco team requests that the guest user also be given EA Admin Read Only access in order to view Cost Management data. The data is used to complete the initial analysis.

### MCA Billing Account Reader (Applies to Microsoft Customer Agreement only)

The Eco team requests that the guest user also be given MCA Billing Account Reader access in order to view Cost Management data. The data is used to complete the initial analysis.

## What's Next?

Learn more about [connecting your account for Eco analysis](eco/getting-started/connect-azure-ea-to-eco).
