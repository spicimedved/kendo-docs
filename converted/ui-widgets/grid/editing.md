---
title: Editing
publish: true
---

### Grid Editing
 <div class="description"> 

To enable the editing support of KendoUI Grid widget the following steps should be performed:

  

#### Configure the DataSource for remote CRUD  (Create, Read, Update, Destroy) data operations:

    var dataSource = new kendo.data.DataSource({
       transport: {
         read:   "/Products",
         update: {
    	    url: "/Products/Update",
    	    type: "POST"
         },
         destroy: {
             url: "/Products/Destroy",
             type: "POST"
          },
          create: {
              url: "/Products/Create",
              type: "POST"
           }
         },
         // determines if changes will be send to the server individually or as batch
         batch: true 
         //...
    });
    `</pre>   

#### Declare fields definition through the DataSource schema:
     <pre class="code prettyprint">`var dataSource = new kendo.data.DataSource({
    //..
    schema: {
      model: {
         id: "ProductID",
         fields: {
             ProductID: { 
                //this field will not be editable (default value is true)
    		editable: false, 
                // a defaultValue will not be assigned (default value is false)
       		nullable: true
    	     },
             ProductName: { 
    		validation: { //set validation rules
    		    required: true 
    		} 
             },
             UnitPrice: { 
                 //data type of the field {Number|String|Boolean} default is String
    		 type: "number", 
                 // used when new model is created
                 defaultValue: 42, 
    		 validation: { 
    		    required: true, 
                    min: 1
    		 }
              }
    	   }
       }
      }
    });
    `</pre>  

    More information on validation rules can be found in [KendoUI Validator article](/documentation/framework/validator/overview.aspx).
      

#### Set the KendoUI Grid editable configuration option:
     <pre class="code prettyprint">`$("#grid").kendoGrid({
      dataSource: dataSource,
      editable: true
    });
    `</pre>  

    or
      

#### Set the KendoUI Grid editable configuration option:
     <pre class="code prettyprint">`$("#grid").kendoGrid({
      dataSource: dataSource,
      editable: { //disables the deletion functionality 
    	 update: true, 
    	 destroy: false
      }
    });
    `</pre>   

#### If you want to enable new records insertion the toolbar should be configured:
     <pre class="code prettyprint">`$("#grid").kendoGrid({
         dataSource: dataSource,
         toolbar: ["create", "save", "cancel"],
         editable: true
     });
    `</pre>   

#### Additionally in order to delete records a delete command column should be defined:
     <pre class="code prettyprint">`$("#grid").kendoGrid({
         dataSource: dataSource,
         columns: [
    		"ProductName", 
    		"UnitPrice", 
    		"UnitsInStock",
    		{ 
    		    command: "destroy"
    		}],
         editable: true
     });

  </div>