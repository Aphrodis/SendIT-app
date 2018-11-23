This web app is called SendIT. 
 
It is a courier service that helps users deliver parcels to different destinations. 

It provides courier quotes based on the weight categories.

ENDPOINTS						

`GET /api/v1/parcels`:Fetch all parcel delivery orders

`GET /api/v1/parcels/:id>`:Fetch a specific parcel delivery order

`GET /api/v1/users/:owner/parcels`:Fetch all parcel delivery orders by a specific user

`PUT /api/v1/parcels/:id/cancel`:Cancel the specific parcel delivery order
	
`POST /api/v1/parcels`:Create a parcel delivery order

RUNNING THE SERVER

nodemon deliveries.js

RUNNING TESTS

npm test
Example about checking if PUT endpoint work:

describe("/PUT parcels/cancel",()=>{
	it("The user with the identified id should be deleted",(done)=>{
		let id ="5";
		chai.request(app).put(`/api/v1/parcels/${id}/cancel`).end((error,res)=>{
			res.should.have.status(200);
			res.body.should.be.a('object');
			done();
		});
	});

	
	it("The person with an identified id should be removed",(done)=>{
		let id ="x";
		chai.request(app).put(`/api/v1/parcels/${id}/cancel`).end((error,res)=>{
			res.should.have.status(404);
			res.body.should.be.a('object');
			done();
		});
	});
});


