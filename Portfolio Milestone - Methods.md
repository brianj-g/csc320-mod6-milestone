# Portfolio Milestone

**Brian Gunther**  
Colorado State University Global  
CSC320: Programming I  
Dr. Gonzalez  
March 24, 2024

The goal of this milestone submission is to introduce the methods of the Automobile and AutomobileInventory classes using Pseudocode. This will ultimately function as an inventory program for a car dealership, per the Portfolio project requirements.

To maintain focus on the methods, the program logic and declaration of variables are implied or abstracted rather than stated in detail.

## Methods for Class: Automobile

The purpose of this class is to hold attributes of a single vehicle, like its vin, make, model, color, and other inherent details. It also contains public methods to construct the object and to update mutable attributes.

### Default Constructor Method

```pseudocode
public Automobile() {
   // Set private class fields to default values
   SET: this.vin TO ""
   SET: this.make TO ""
   SET: this.model TO ""
   SET: this.color TO ""
   SET: this.year TO -1
   SET: this.mileage TO 0
}
```

### Parameterized Constructor Method

```pseudocode
public Automobile(String vin, String make, String model, String color, int year, int mileage) {
   // Set private class fields to parameter values
   SET: this.vin TO vin
   SET: this.make TO make
   SET: this.model TO model
   SET: this.color TO color
   SET: this.year TO year
   SET: this.mileage TO mileage
}
```

### Update Color Attribute

```pseudocode
public void updateColor(String color) {
   // Set private class field to parameter value
   SET: this.color TO color
}
```

### Update Mileage Attribute

```pseudocode
public void updateMileage(int mileage) {
   // Set private class field to parameter value
   SET: this.mileage TO mileage
}
```

### Get VIN

```pseudocode
public String getVin() {
   RETURN: value of the private variable "vin"
}
```

## Methods for Class: AutomobileInventory

The purpose of this class is to provide a user interface for accessing and using the inventory. This class will contain an ArrayList of type Automobile which holds the objects.

### Add New Vehicle

```pseudocode
public boolean addVehicle(String vin, String make, String model, String color, int year, int mileage) {
   TRY:
      SEARCH inventory for vin
      IF vin does not already exist:
            INSTANTIATE a new object of type Automobile using the provided parameters
            RETURN True
      ELSE:
         RETURN False
   EXCEPT:
      Log exception
      RETURN False
}
```

### Remove a Vehicle

```pseudocode
public boolean removeVehicle(String vin) {
   TRY:
      SEARCH inventory arraylist for the vin
      IF found:
            DELETE vehicle from arraylist
            RETURN True
      ELSE:
         RETURN False
   EXCEPT:
      Log exception
      RETURN False
}
```

### Retrieve Vehicle Information

```pseudocode
public Automobile showVehicle(String vin) {
   INSTANTIATE a new empty Automobile object "vehicle"
   TRY:
      SEARCH inventory arraylist for the vin provided and store in "vehicle"
      IF found:
         RETURN vehicle
      ELSE:
         RETURN null
   EXCEPT:
      Log exception
      RETURN null
}
```

### Update Vehicle Attributes

Note that only the alterable attributes like mileage and color can change. The Vin, Year, Make, Model should never change.

```pseudocode
public boolean updateAttribute(String vin, String attribute, String value) {
   TRY:
      SEARCH inventory arraylist for the vin
      IF found:
         VALIDATE attribute, RETURN False if invalid

         IF attribute is type int:
            TRY:
               CONVERT value to int
            EXCEPT:
               Log exception
               RETURN False

         SWITCH attribute:
            mileage: CALL updateMileage
            color:   CALL updateColor
            default: RETURN False

         RETURN True
      ELSE:
         RETURN False
   EXCEPT:
      Log exception
      RETURN False
}
```

### List All Vehicles

```pseudocode
public void showAllVehicles() {
   TRY:
      FOR EACH Automobile object in the arraylist:
         PRINT LINE: Vin, Make, Model, Color, Year, Mileage
   EXCEPT:
      Log exception
}
```