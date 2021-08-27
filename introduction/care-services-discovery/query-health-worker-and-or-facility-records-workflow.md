# Query Health Worker and/or Facility Records Workflow

 ****Workflow for a point of service application to query the Info Manager for health workers, facilities and/or the services provided by each.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh5.googleusercontent.com/JtMiFMfprHsm6bp5bPjwqbjk7lTXHFOmWF6hvgxXCOpsdz7FEWQnuyjwaCnkTfyCG-fOtIfz6TtqGkwHNHL1kQH0-R-JzEC6LngazcAgioSUd7b5qlvsaEqqrYfJrOrZlQ"
          alt/>
        </p>
        <p><b>  Maturing</b>
        </p>
      </th>
      <th style="text-align:left">
        <p></p>
        <ul>
          <li>Workflow is defined and ARB Approved</li>
          <li>Workflow is supported by CSD IHE standards*</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Care Services Discovery (CSD): ftp://ftp.ihe.net/DocumentPublication/CurrentPublished/ITInfrastructure/IHE_ITI_Suppl_CSD.pdf</td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>IL = Interoperability Layer to handle data governance and security issues,
            CSD Services Finder</li>
          <li>POS = Point of Service Application, CSD Services Finder</li>
          <li>ILR InfoMan = Interlinked Registries CSD InfoManager</li>
          <li>HWR = Health Worker Registry HWR, CSD Services Directory</li>
          <li>FR = Facility Registry FR, CSD Services Directory</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description** 

The following is a description of the interaction steps. ****

![](https://lh4.googleusercontent.com/jqfTIzdr175wG-QVNwzNs4kz8VY7prz8-qKSIMDtGbDElOQuqeh4emBBeG8K1OZjI6ApLq6OIILrGcCQMqlsZkGdWyxQlz5QLOwnbD3mFaF_waA9fH2F_nIk_TxVFCdJ6A)

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>#</b>
      </th>
      <th style="text-align:left"><b>Interaction</b>
      </th>
      <th style="text-align:left"><b>Data / Notes</b>
      </th>
      <th style="text-align:left"><b>Transaction Options</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0</td>
      <td style="text-align:left">Initiated according to timing set by jurisdiction</td>
      <td style="text-align:left">HTTP GET Request. No query parameters required.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Request Added / Updated facilities</td>
      <td style="text-align:left">POST SOAP wrapped message with last time service directory was polled</td>
      <td
      style="text-align:left">[ITI-74] Query for Updated Services Transaction</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Return Added / Updated facilities</td>
      <td style="text-align:left">SOAP wrapped CSD document with updates to services (facilities)</td>
      <td
      style="text-align:left">[ITI-74] Query for Updated Services Transaction</td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Request Added / Updated Providers</td>
      <td style="text-align:left">SOAP wrapped message with last time service directory was polled</td>
      <td
      style="text-align:left">[ITI-74] Query for Updated Services Transaction</td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Return Added / Updated Providers</td>
      <td style="text-align:left">SOAP wrapped CSD document with updates to services (health workers)</td>
      <td
      style="text-align:left">[ITI-74] Query for Updated Services Transaction</td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">Merge Facilities and Providers</td>
      <td style="text-align:left">
        <p>(Optional)</p>
        <p>Merge caches of FR and HWR according to jurisdiction specific data governance/conflict
          resolution policy</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">Merge response</td>
      <td style="text-align:left">
        <p>HTTP 200 Response on success.</p>
        <p>HTTP 500 Response on failure</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Find Matching Services Request</td>
      <td style="text-align:left">POST careServicesRequest document defined in CSD.xsd</td>
      <td style="text-align:left">[ITI-73] Find Matching Services (Ad-Hoc and Stored)</td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">Ensure PoS has access rights</td>
      <td style="text-align:left">@uuid attribute in careServicesRequest document for stored queries is
        used for validation</td>
      <td style="text-align:left">
        <p>Validation is defined according to country specific</p>
        <p>Data governance policies in accessing the InfoMan</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">XQuery for content</td>
      <td style="text-align:left">POST careServicesRequest document defined in CSD.xsd</td>
      <td style="text-align:left">[ITI-73] Find Matching Services (Ad-Hoc and Stored)</td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">Return content</td>
      <td style="text-align:left">Result of executing stored referencced by uuid/ad-hoc xquery. Usually
        a CSD document but can have any content-type depending on the query requested.</td>
      <td
      style="text-align:left">[ITI-73] Find Matching Services (Ad-Hoc and Stored)</td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">Find Matching Services Response</td>
      <td style="text-align:left">Result of executing stored referencced by uuid/ad-hoc xquery. Usually
        a CSD document but can have any content-type depending on the query requested.</td>
      <td
      style="text-align:left">[ITI-73] Find Matching Services (Ad-Hoc and Stored)</td>
    </tr>
  </tbody>
</table>

