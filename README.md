// User class to store user information
class User {
  constructor(name, email, password) {
    this.name = name;
    this.email = email;
    this.password = password;
    this.listings = [];
  }
}

// Listing class to store information about food items available for swap
class Listing {
  constructor(user, item, description, imageUrl) {
    this.user = user;
    this.item = item;
    this.description = description;
    this.imageUrl = imageUrl;
    this.offers = [];
  }

  // Method to add an offer to the listing
  addOffer(offer) {
    this.offers.push(offer);
  }
}

// Offer class to store information about a swap offer
class Offer {
  constructor(user, item, message) {
    this.user = user;
    this.item = item;
    this.message = message;
  }
}

// App class to handle app functionality
class App {
  constructor() {
    this.users = [];
    this.listings = [];
  }

  // Method to register a new user
  registerUser(name, email, password) {
    const user = new User(name, email, password);
    this.users.push(user);
    return user;
  }

  // Method to create a new listing
  createListing(user, item, description, imageUrl) {
    const listing = new Listing(user, item, description, imageUrl);
    this.listings.push(listing);
    user.listings.push(listing);
    return listing;
  }

  // Method to make an offer on a listing
  makeOffer(listing, user, item, message) {
    const offer = new Offer(user, item, message);
    listing.addOffer(offer);
    return offer;
  }
}

// Example usage:

const app = new App();

// Register a new user
const user1 = app.registerUser("John Smith", "john@example.com", "password123");

// Create a new listing for homemade jam
const listing1 = app.createListing(user1, "Homemade strawberry jam", "Delicious jam made from fresh strawberries", "https://example.com/jam.jpg");

// Make an offer on the listing
const user2 = app.registerUser("Jane Doe", "jane@example.com", "password456");
const offer1 = app.makeOffer(listing1, user2, "Homemade pickles", "I would love to try your jam! Would you be interested in some homemade pickles in exchange?");

// Display the listing and its offers
console.log(listing1);
console.log(listing1.offers);
