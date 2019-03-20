# Access Control Policies

A collection of examples of both DAC and MAC policies. 

## Examples

### MAC

1. `Software Example` is a simple MAC policy which restricts access to the software classification of part. Users outside of the employee identity are unable to view software parts, but can view all other classifications of part. This is designed to show how you can leverage properties on ItemTypes to create restrictive policies.
   
2. `Time Example` is an example which shows off the use of an Environment Attribute. Environment Attributes contain methods which return a value, which can be used in your MAC rules. In this example, the method officeHour returns true if it is during office hours, and false otherwise. We use this method in the rule, to restrict access to assemblies outside of office hours. 
   
3. `Hide Classified Parts` is an example which adds a property `is_classified` to part. Any part which is marked as classified will be hidden from all users except employees. Adding a similar property to the user ItemType would allow for finer control of access. 

4. `Hide Previous Revisions` Is an example which hides all previous revisions of parts from users. Employees are able to view and interact with any revision of the parts.

### DAC
**Note: Conversion server must be configured to create DAC Policies**

1. `Parts related to Project` is a very smiple DAC policy. It defines unique permissions for the collection of parts which are associated with a given project. You can assign a specific team to a project utilizing this DAC policy to see it in action.

 

## History


Release | Notes
--------|--------

[v1.0](https://github.com/ArasLabs/Access-Control-Policies/releases/tag/v1.0) | First release. Built and tested in 11.0 SP15

#### Supported Aras Versions

Project | Aras
--------|------

[v1.0](https://github.com/ArasLabs/Access-Control-Policies/releases/tag/v1.0) | 11.0 SP15

## Installation

#### Important!
**Always back up your code tree and database before applying an import package or code tree patch!**

### Pre-requisites

1. Aras Innovator installed (version 11.0 SP15 preferred)
2. Aras Conversion Server configured
3. Aras Package Import tool

### Install Steps


1. Backup your database and store the BAK file in a safe place.
2. Open up the Aras Package Import tool.
3. Enter your login credentials and click **Login**
    * _Note: You must login as root for the package import to succeed!_
4. Enter the package name in the TargetRelease field.
    * Optional: Enter a description in the Description field.
5. Enter the path to your local `..\Imports\imports.mf` file in the Manifest File field.
6. Select the following in the Available for Import field.
    * **aras.labs.policies**
    * **com.aras.innovator.solution.PLM**
    * **com.aras.innovator.ACExtensions**
7. Select Type = **Merge** and Mode = **Thorough Mode**.
8. Click **Import** in the top left corner.
9. Close the Aras Package Import tool.

You are now ready to login to Aras and try out the Example Access Control Examples
## Usage

### DAC Policies

**Pre-requisite:** The Conversion server must be configured to generate `dr_DepartureItems`

1. Log in to Aras as admin.
2. Navigate to **Administration > Configuration > Derived Relationship Families**.
3. Promote the `Part Related to Project` item to `Persisting`
4. Navigate to the `Part Related to Project` DAC and promote it to Active
5. Test it out!

### MAC Policies

1. Log in to Aras as admin.
2. Navigate to **Administration > Access > MAC Policies**
3. Open and activate any policies you wish to test!


## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

For more information on contributing to this project, another Aras Labs project, or any Aras Community project, shoot us an email at araslabs@aras.com.

## Credits

Created by AJ Sebastian for Aras Labs.

## License

Aras Labs projects are published to Github under the MIT license. See the [LICENSE file](./LICENSE.md) for license rights and limitations.
