# Group-based access control

Here are the exact steps to implement Row-Level Security (RLS) using User Groups in Tableau:

1.  **Create User Groups**
    *   Log in to **Tableau Server** or **Tableau Cloud**.
    *   Navigate to **Groups** and create your groups (e.g., "East Team", "West Team", "Managers").
    *   Add the appropriate users to each group.

2.  **Create a Calculated Field**
    *   Open **Tableau Desktop** and connect to your data.
    *   Select **Analysis** > **Create Calculated Field**.
    *   Enter a name (e.g., "User Filter") and use a formula that maps groups to data values.
    *   *Example Formula:*
        ```tableau
        (ISMEMBEROF('Managers')) -- Managers see all
        OR
        (ISMEMBEROF('East Team') AND [Region] = 'East')
        OR
        (ISMEMBEROF('West Team') AND [Region] = 'West')
        ```

3.  **Apply the Filter**
    *   Drag the new calculated field to the **Filters** shelf.
    *   Select **True**.
    *   (Optional) To apply to all sheets, right-click the filter in the shelf and select **Apply to Worksheets** > **All Using This Data Source**.
