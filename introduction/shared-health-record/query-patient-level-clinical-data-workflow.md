# Query Patient-level Clinical Data Workflow

 ****The transaction queries for previously stored clinical data for a specific patient. The following sequence diagram shows the steps involved in this transaction.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh5.googleusercontent.com/Vp6XBRGu-U_Dmd5EKNpCZvEEum0CxOcHOj9NgHh8UMMNLMlXHmLcUE_YWueDRr4uqWLzpPfzSBLJ2k33XQIelLypjQ4wyrD17-t33GtLa8fFxW9AYDvXhiJmBl4VaLgKDg"
          alt/>
        </p>
        <p><b>    Mature</b>
        </p>
      </th>
      <th style="text-align:left">
        <p></p>
        <ul>
          <li><b>One or more OpenHIE implementations of this workflow exist  in one or more countries</b>
          </li>
          <li><b>Workflow is defined and ARB approved</b>
          </li>
          <li><b>Workflow is supported by mature standards</b>
          </li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>XDS.b with the on-demand document option</li>
          <li>CDA documents profiled by IHE PCC</li>
          <li>CSD - Find matching services - ITI-73</li>
          <li>PIX Query - ITI-9</li>
          <li><b>Optionally</b>, the MHD profile can be supported (in addition or instead
            of XDS.b) to enable PoC systems to query clinical content using a simpler
            and more modern FHIR-based approach. This option may be supported in two
            ways:
            <ul>
              <li>The SHR itself may support the required MHD transactions.</li>
              <li>(<b>recommended</b>) The IL can provide an adapter to convert incoming
                MHD transactions to XDS.b transactions for the SHR to process as normal.</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>The PoS system must ensure the patient they are querying clinical information
            about already exists. It can do this by querying for the patient (<a href="https://docs.google.com/document/d/1vn46_f0nKDSwiSNfU1JzCat0sFvHe8y3mM5Py2nz4uU/edit#heading=h.i2zmb6glro23">Query patients workflow</a>).</li>
          <li>The PoS system is a trusted application known by the HIE and it is registered
            with the interoperability layer to be able to send and receive data securely
            (<a href="https://wiki.ohie.org/display/documents/Common+message+security+workflow">Common message security workflow</a>).</li>
        </ul>
        <p>The SHR<b> MUST</b> be able to generate on-demand documents in the <a href="http://wiki.ihe.net/index.php?title=Medical_Summaries_Profile">XDS-MS</a> format
          using the data it stored in the <a href="https://docs.google.com/document/d/1vn46_f0nKDSwiSNfU1JzCat0sFvHe8y3mM5Py2nz4uU/edit#heading=h.rldiwp20bk7f">save patient-level clinical data workflow</a>.
          Optionally, any other sections that have been discretely imported and are
          deemed useful may be added to the generated XDS-MS document.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point of care system that captures a patient&apos;s clinical
            encounter, it is responsible for sending clinical data on to the HIE.</li>
          <li>IL - Mediates the transactions between the PoS system and the infrastructure
            services to facilitate easier interoperability.</li>
          <li>CR - The source of truth for patient demographic and identifier detail.
            It is able to be queried using an identifier to find the enterprise identifier
            for a particular person.</li>
          <li>FR - The source of truth for facility information. It is able to be queried
            for details about a particular facility by ID.</li>
          <li>SHR - Stored patients clinical information. It is able to receive and
            store patient clinical documents.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description** 

The following is a description of the interaction steps. 

![](https://lh3.googleusercontent.com/pdTH8pA1_8ukXlAAVEYWMWGGdnkfEo2CfGe3_8S8GTMGXG0U6kE92bQIZ59C40w-47VlphCZnw0C0c-rkZD0fiwHvKiG5QKC3jSowHX4QAOx_lnpuyH9HuOyYHLI6MPkeA)

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left">Interaction</th>
      <th style="text-align:left">Data</th>
      <th style="text-align:left">Transaction Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Query for clinical documents by patient ID and/or date</td>
      <td style="text-align:left">
        <p>XDS.b/MHD metadata</p>
        <p>Option 1 (must be supported): XDS.b Registry Stored Query (ITI-18) - Find
          Documents query</p>
        <p>OR</p>
        <p>Option 2 (may additionally choose to support): MHD Find document references
          (ITI-67) - RESTful query
          <br />
          <br />
        </p>
      </td>
      <td style="text-align:left">
        <p><a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 10, Appendix E, J, K</p>
        <p>Vol. 2a - Sections 3.18</p>
        <p>Vol. 2b - Sections 3.41, 3.42, 3.43</p>
        <p>Vol. 2x - Appendix A, B, K, L, M, N, V, W</p>
        <p>Vol. 3 - Section 4.1, 4.2, 4.3If supporting the MHD Option: <a href="http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_MHD.pdf">MHD profile supplement</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Resolve client identifier</td>
      <td style="text-align:left">HL7 QBP^Q23 message</td>
      <td style="text-align:left">
        <p>PIX Query (ITI-9) <a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 5</p>
        <p>Vol. 2 - Sections 3.9</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Return person record</td>
      <td style="text-align:left">HL7 RSP^K23 message</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Extract ECID and enrich message with ECID</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">Query for clinical documents by ECID</td>
      <td style="text-align:left">
        <p>XDS.b/MHDmetadata</p>
        <p>XDS.b Registry Stored Query (ITI-18) - Find Documents query</p>
        <p>and optionally (only if SHR support MHD directly)</p>
        <p>MHD Find document references (ITI-67) - RESTful query
          <br />
          <br />
        </p>
      </td>
      <td style="text-align:left">
        <p><a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 10, Appendix E, J, K</p>
        <p>Vol. 2a - Sections 3.18</p>
        <p>Vol. 2b - Sections 3.41, 3.42, 3.43</p>
        <p>Vol. 2x - Appendix A, B, K, L, M, N, V, W</p>
        <p>Vol. 3 - Section 4.1, 4.2, 4.3MHD: <a href="http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_MHD.pdf">MHD profile supplement</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">Return list of document IDs</td>
      <td style="text-align:left">
        <p>XDS.b Registry Stored Query response - list of document IDs</p>
        <p>or optionally (only if SHR support MHD directly)</p>
        <p>MHD Find document references response - list of document IDs</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Return list of document IDs</td>
      <td style="text-align:left">
        <p>XDS.b Registry Stored Query response - list of document IDs</p>
        <p>or optionally</p>
        <p>MHD Find document references response - list of document IDs</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">Request the content of the document by document ID</td>
      <td style="text-align:left">
        <p>XDS.b/MHDmetadata</p>
        <p>XDS.b Retrieve Document Set (ITI-43)</p>
        <p>and optionally</p>
        <p>MHD Retrieve document (ITI-68)
          <br />
          <br />
        </p>
      </td>
      <td style="text-align:left">
        <p><a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 10, Appendix E, J, K</p>
        <p>Vol. 2a - Sections 3.18</p>
        <p>Vol. 2b - Sections 3.41, 3.42, 3.43</p>
        <p>Vol. 2x - Appendix A, B, K, L, M, N, V, W</p>
        <p>Vol. 3 - Section 4.1, 4.2, 4.3MHD: <a href="http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_MHD.pdf">MHD profile supplement</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">Request the content of the document by document ID</td>
      <td style="text-align:left">
        <p>XDS.b/MHDmetadata</p>
        <p>XDS.b Retrieve Document Set (ITI-43)</p>
        <p>and optionally (only if SHR support MHD directly)</p>
        <p>MHD Retrieve document (ITI-68)
          <br />
          <br />
        </p>
      </td>
      <td style="text-align:left">
        <p><a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 10, Appendix E, J, K</p>
        <p>Vol. 2a - Sections 3.18</p>
        <p>Vol. 2b - Sections 3.41, 3.42, 3.43</p>
        <p>Vol. 2x - Appendix A, B, K, L, M, N, V, W</p>
        <p>Vol. 3 - Section 4.1, 4.2, 4.3MHD: <a href="http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_MHD.pdf">MHD profile supplement</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">
        <p>If this document is a static document retrieve it</p>
        <p>else if it is an on-demand document generate it</p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">For ODD: <a href="http://wiki.ihe.net/index.php?title=Medical_Summaries_Profile">XDS-MS Specification</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">Return clinical document</td>
      <td style="text-align:left">XDS.b/MHDresponse - with CDA document content</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">12</td>
      <td style="text-align:left">Return clinical document</td>
      <td style="text-align:left">XDS.b/MHDresponse - with CDA document content</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>



{% hint style="success" %}
References:  [WHO DDCC Workflows](https://worldhealthorganization.github.io/ddcc/workflows.html)
{% endhint %}

