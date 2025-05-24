---
# NOTICE: Copyright 2025 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "EnvoieCarte"
    version: "4.1.0"
    description: "An API for managing a list of tasks that need to be done"
    license: {}
    contact: {}
    termsOfService: ""
  contract:
    mediaTypes:
    - "application/json"
    unsortedElementOrder:
    - "#/contract/resources/5b1d3846-1e16-4624-8dba-69e5e741485a"
    - "#/contract/resources/038f9a96-de43-4eb6-8199-69bf0974c18b"
    - "#/contract/types/46917aee-4a9d-4147-bdb4-2cb3bd741651"
    - "#/contract/types/20aff05a-1b52-4ff4-95b3-a7ed86274942"
    - "#/contract/resources/36866066-91a0-41c9-adab-9a1949d52bfa"
    securitySchemes:
      e1536907-75a0-4f63-86fb-04c606e4f010:
        name: "HTTP_BASIC"
        type: "basic"
        description: "All GET methods are public, meaning that *you can read all the data*. Write operations require authentication and therefore are forbidden to the general public."
        describedBy: {}
    resources:
      "5b1d3846-1e16-4624-8dba-69e5e741485a":
        path: "/tasks/"
      "038f9a96-de43-4eb6-8199-69bf0974c18b":
        path: "/tasks/{taskid}"
        pathVariables:
        - name: "taskid"
          type: "STRING"
          description: "Identifier of the Task"
          examples:
          - value: "47ee3550-b619-11e6-8408-0bdb025a7cfa"
        operations:
          a0a4d2ca-b40c-43f2-8d14-c96cd9e648dc:
            name: "Load a specific Task"
            method: "GET"
            responses:
              bcf3db48-4656-4d6d-8bcd-f3619d51b3e7:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/46917aee-4a9d-4147-bdb4-2cb3bd741651"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
              "6f8044e3-d6bc-497c-a572-0fa4d4579dcb":
                status: "400"
                description: "Status 400"
                bodies:
                - type: "#/contract/types/20aff05a-1b52-4ff4-95b3-a7ed86274942"
          "83bdbc13-4c9a-40e1-bcf5-d62316a88f9f":
            name: "Update a Task"
            method: "PUT"
            securedBy:
            - scheme: "#/contract/securitySchemes/e1536907-75a0-4f63-86fb-04c606e4f010"
              scopes: []
            bodies:
            - type: "#/contract/types/46917aee-4a9d-4147-bdb4-2cb3bd741651"
              examples:
              - value: |-
                  {
                    "name": "Feed the fish",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              "05866969-813f-43c5-ab48-8db89a6a0074":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/46917aee-4a9d-4147-bdb4-2cb3bd741651"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
          "725ec062-deac-4b3e-babb-9b8c9c75c2ac":
            name: "Delete a Task"
            method: "DELETE"
            securedBy:
            - scheme: "#/contract/securitySchemes/e1536907-75a0-4f63-86fb-04c606e4f010"
              scopes: []
            responses:
              "0d8e6b58-d6d5-4d2e-97c1-9f92a29c030c":
                status: "200"
                description: "Status 200"
      "36866066-91a0-41c9-adab-9a1949d52bfa":
        path: "/tasks/Service/EnvoieCarte"
        operations:
          f3408586-74a7-4818-b197-8943a8fb9c97:
            name: "Load the list of Tasks"
            method: "GET"
            queryParameters:
            - name: "$size"
              type: "INTEGER"
              description: "Size of the page to retrieve."
              examples:
              - value: 10
            - name: "$page"
              type: "INTEGER"
              description: "Number of the page to retrieve."
              examples:
              - value: 1
            - name: "$sort"
              type: "STRING"
              description: "Order in which to retrieve the results. Multiple sort criteria can be passed."
              examples:
              - value: "createdAt DESC"
              - value: "name ASC"
            - name: "id"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `id`"
              examples:
              - value: "47ee3550-b619-11e6-8408-0bdb025a7cfa"
            - name: "name"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `name`"
              examples:
              - value: "Learn about hypermedia APIs"
            - name: "createdAt"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `createdAt`"
              examples:
              - value: "2016.07.03"
            - name: "completed"
              type: "BOOLEAN"
              description: "Allows to filter the collection of results by the value of field `completed`"
              examples:
              - value: true
              - value: false
            - name: "SiteCode"
              type: "STRING"
              description: "Site code"
              required: true
              examples:
              - value: "1,2,558"
            headers:
            - name: "Key"
              type: "STRING"
              description: "Key for authentification"
              required: true
            responses:
              e79ed5a8-5fa9-4141-a158-4b48de28f480:
                status: "200"
                description: "Status 200"
                headers:
                - name: "X-Page-Count"
                  type: "INTEGER"
                  examples:
                  - value: 1
                - name: "X-Page-Number"
                  type: "INTEGER"
                  examples:
                  - value: 1
                - name: "X-Page-Size"
                  type: "INTEGER"
                  examples:
                  - value: 25
                - name: "X-Total-Count"
                  type: "INTEGER"
                  examples:
                  - value: 2
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/46917aee-4a9d-4147-bdb4-2cb3bd741651"
                  examples:
                  - value: |-
                      [{
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }]
              "622f535e-9898-4b0b-ba05-b08f8fc92b8d":
                status: "400"
                description: "Status 400"
                bodies:
                - type: "#/contract/types/20aff05a-1b52-4ff4-95b3-a7ed86274942"
          e4b8314f-fb89-4c7f-8504-bae654358024:
            name: "Create a new task"
            method: "POST"
            securedBy:
            - scheme: "#/contract/securitySchemes/e1536907-75a0-4f63-86fb-04c606e4f010"
            bodies:
            - type: "#/contract/types/46917aee-4a9d-4147-bdb4-2cb3bd741651"
              examples:
              - value: |-
                  {
                    "name": "Feed the fish",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              f385b804-24ea-4d37-9760-f00df04595c6:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/46917aee-4a9d-4147-bdb4-2cb3bd741651"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
    types:
      "46917aee-4a9d-4147-bdb4-2cb3bd741651":
        name: "Task"
        type: "OBJECT"
        description: "An object that represents a task"
        properties:
        - name: "id"
          type: "STRING"
          description: "Auto-generated primary key field"
          required: true
          examples:
          - value: "3fa2eb40-b61c-11e6-9de0-fdbe71bceebb"
        - name: "name"
          type: "STRING"
          required: true
          examples:
          - value: "Figure out how to colonize Mars"
        - name: "completed"
          type: "BOOLEAN"
          required: true
        - name: "createdAt"
          type: "STRING"
          examples:
          - value: "2016.10.06"
        examples:
        - value: |-
            {
              "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
              "name": "Feed the fish",
              "completed": false,
              "createdAt": "2016.07.03"
            }
      "20aff05a-1b52-4ff4-95b3-a7ed86274942":
        name: "Error"
        type: "OBJECT"
        description: "This general error structure is used throughout this API."
        properties:
        - name: "code"
          type: "INTEGER"
          required: true
          minimum: 400
          maximum: 599
        - name: "description"
          type: "STRING"
          examples:
          - value: "Bad query parameter [$size]: Invalid integer value [abc]"
          - value: "The server understood the request, but is refusing to fulfill it"
        - name: "reasonPhrase"
          type: "STRING"
          examples:
          - value: "Bad Request"
          - value: "Forbidden"
        examples:
        - value: |-
            {
              "code": 400,
              "description": "Bad query parameter [$size]: Invalid integer value [abc]",
              "reasonPhrase": "Bad Request"
            }
  components: {}
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "EnvoieCarte 4.1.0",
        "description" : "An API for managing a list of tasks that need to be done",
        "importedFrom" : "b93b038d-3e5a-4d28-8608-a28df2c2a4da"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "a0a4d2ca-b40c-43f2-8d14-c96cd9e648dc",
          "name" : "Load a specific Task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
          },
          "method" : {
            "link" : "",
            "name" : "GET"
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "83bdbc13-4c9a-40e1-bcf5-d62316a88f9f",
          "name" : "Update a Task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
          },
          "method" : {
            "link" : "",
            "name" : "PUT",
            "requestBody" : true
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Content-Type",
            "value" : "application/json"
          }, {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form",
          "body" : {
            "bodyType" : "Text",
            "textBody" : "{\n  \"name\": \"Feed the fish\",\n  \"completed\": false,\n  \"createdAt\": \"2016.07.03\"\n}"
          }
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "725ec062-deac-4b3e-babb-9b8c9c75c2ac",
          "name" : "Delete a Task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
          },
          "method" : {
            "link" : "",
            "name" : "DELETE"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "f3408586-74a7-4818-b197-8943a8fb9c97",
          "name" : "Load the list of Tasks",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/Service/EnvoieCarte",
            "query" : {
              "delimiter" : "&",
              "items" : [ {
                "name" : "$size",
                "value" : "10",
                "enabled" : false
              }, {
                "name" : "$page",
                "value" : "1",
                "enabled" : false
              }, {
                "name" : "$sort",
                "value" : "createdAt DESC",
                "enabled" : false
              }, {
                "name" : "id",
                "value" : "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                "enabled" : false
              }, {
                "name" : "name",
                "value" : "Learn about hypermedia APIs",
                "enabled" : false
              }, {
                "name" : "createdAt",
                "value" : "2016.07.03",
                "enabled" : false
              }, {
                "name" : "completed",
                "value" : "true",
                "enabled" : false
              }, {
                "name" : "SiteCode",
                "value" : "1,2,558",
                "enabled" : true
              } ]
            }
          },
          "method" : {
            "link" : "",
            "name" : "GET"
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Key",
            "value" : ""
          }, {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form",
          "uriEditor" : true
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "e4b8314f-fb89-4c7f-8504-bae654358024",
          "name" : "Create a new task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/Service/EnvoieCarte"
          },
          "method" : {
            "link" : "",
            "name" : "POST",
            "requestBody" : true
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Content-Type",
            "value" : "application/json"
          }, {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form",
          "body" : {
            "bodyType" : "Text",
            "textBody" : "{\n  \"name\": \"Feed the fish\",\n  \"completed\": false,\n  \"createdAt\": \"2016.07.03\"\n}"
          }
        }
      } ]
    } ],
    "environments" : [ {
      "name" : "EnvoieCarte 4.1.0",
      "importedFrom" : {
        "projectId" : "b93b038d-3e5a-4d28-8608-a28df2c2a4da"
      },
      "variables" : {
        "de7dfcae-ed9f-4da6-bc31-0f5a558901e3" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
