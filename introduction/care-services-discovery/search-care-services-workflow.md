# Search Care Services Workflow

Workflow for a point of service application to query a Care Services registry for health workers, facilities, organizations, and/or the services provided by each.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Standards*</th>
      <th style="text-align:left"><b>Mobile Care Services Discovery (mCSD): ftp://ftp.ihe.net/DocumentPublication/CurrentPublished/ITInfrastructure/IHE_ITI_Suppl_mCSD.pdf</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left">
        <p>A Care Services Registry shall have one or more of the following resources:</p>
        <ul>
          <li>Location</li>
          <li>Practitioner and PractitionerRole</li>
          <li>Organization</li>
          <li>HealthcareService</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left">
        <ul>
          <li>PoS = Point of Service Application, mCSD Care Services Selective Consumer</li>
          <li>ILR InfoMan = Interlinked Registry, mCSD Care Services Selective Supplier</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description**

The following is a description of the interaction steps.

![](https://lh3.googleusercontent.com/02eui3Y7oh1OzSYl2zzilg7gZfX8pEfJfvw2tNmvrFZg3TRmzjGsJmSFx5y3xqzRRamwKxJOoM2Z36SBgEmwy1fQ3yc-BAsevaBPw5ppor75EZIjDHTPQhQ3FTXwoKfkPQ)

| **\#** | **Interaction** | **Data / Notes** | **Transaction Options** |
| :--- | :--- | :--- | :--- |
| 1 | Search for matching care services | HTTP GET Request with optional query parameters.  Can be for any supported resources. | \[ITI-90\] Find Matching Care Services |
| 2 | Return matching care services | HTTP response with FHIR Bundle of matching resources or an error if an invalid request or server error. | \[ITI-90\] Find Matching Care Services |

## \*\*\*\*

