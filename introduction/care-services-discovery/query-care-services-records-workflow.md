# Query Care Services Records Workflow

Workflow for a point of service application to query the Info Manager for the care services provided by each.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh3.googleusercontent.com/5pqeaiKmzar1ArIa8oQG4D_pt1AUs6-4_d5KLJXFLpkp1PdN4eYtUD5YcMO0YNTHEH4OkUp5Jom_Gy56jgz-2o5kGTV9QtIBtg79TYH2wWecLI6PzT4uXwuBlbBKPagbDw"
          alt/>
        </p>
        <p><b>  Maturing</b>
        </p>
      </th>
      <th style="text-align:left">
        <p></p>
        <ul>
          <li>Workflow is defined and ARB Approved</li>
          <li>Workflow is supported by emerging IHE mCSD standard</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Mobile Care Services Discovery (mCSD): ftp://ftp.ihe.net/DocumentPublication/CurrentPublished/ITInfrastructure/IHE_ITI_Suppl_mCSD.pdf</td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
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
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>IL = Interoperability Layer to handle data governance and security issues,
            mCSD Care Services Selective Supplier</li>
          <li>PoS = Point of Service Application, mCSD Care Services Selective Consumer</li>
          <li>ILR InfoMan = Interlinked Registries mCSD Care Services Update Consumer
            and Care Services Selective Supplier</li>
          <li>HWR = Health Worker Registry HWR, mCSD Care Services Update Supplier</li>
          <li>FR = Facility Registry FR, mCSD Care Services Update Supplier</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description** 

The following is a description of the interaction steps.

![](https://lh4.googleusercontent.com/iVCaCslsAsJcMknAmDxB5EZCywa0jMwt4FlxRHWXexw7S1jkKo5VwwipBh8ZkvkLsjQ3ivOjhrXYgrpE5L89XqYucK-9tgXIDHS4l3eTntlLbwjFRZVu4ayrePi44iupWg)

| **\#** | **Interaction** | **Data / Notes** | **Transaction Options** |
| :--- | :--- | :--- | :--- |
| 0 | Initiated according to timing set by jurisdiction | HTTP GET Request.  No query parameters required. |  |
| 1 | Request Added / Updated healthcare worker data | HTTP GET Request.  Optional parameter since a requested time. | \[ITI-91\] Request Care Services Updates Request |
| 2 | Return Added / Updated healthcare worker data | HTTP response with FHIR Bundle. | \[ITI-91\] Request Care Services Updates Response |
| 3 | Save or Merge healthcare worker data | Save or optionally merge updated data based on jurisdictional requirements. |  |
| 4 | Return Added / Updated facility data | HTTP GET Request.  Optional parameter since a requested time. | \[ITI-91\] Request Care Services Updates Request |
| 5 | Return Added / Updated healthcare worker data | HTTP response with FHIR Bundle. | \[ITI-91\] Request Care Services Updates Response |
| 6 | Save or Merge healthcare worker data | Save or optionally merge updated data based on jurisdictional requirements |  |
| 7 | Search for matching interlinked data from PoS to IL. | HTTP GET Request with optional query parameters.  Can be for any supported resources. | \[ITI-90\] Find Matching Care Services Request |
| 8 | Forward search for matching interlinked data from IL to ILR if access is allowed. | HTTP GET Request with optional query parameters.  Can be for any supported resources. | \[ITI-90\] Find Matching Care Services Request |
| 9 | Return matching care services from ILR to IL | HTTP response with FHIR Bundle of matching resources or an error if an invalid request or server error. | \[ITI-90\] Find Matching Care Services Response |
| 10 | Return matching care services from IL to PoS | HTTP response with FHIR Bundle of matching resources or an error if an invalid request or server error. | \[ITI-90\] Find Matching Care Services Response |
| 11 | If PoS doesn’t have access return error | Return invalid access error. |  |

## \*\*\*\*

