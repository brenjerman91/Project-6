/*
Name: Benjamin Jensen 

Class: CIT 281 
*/
/*
function displayFunction(sum, num){
    //console.log (`Total: ${sum}; Num: ${num}`)
    return sum + num;
}
*/
class Shape {
    constructor(sides) {
        this.sides = sides;
    }
    perimeter = () => {
        return this.sides ? this.sides.reduce((sum, num) => sum + num) : 0
    }
};



/*
console.log(new Shape([5, 10]).perimeter());
console.log(new Shape([1, 2, 3, 4, 5]).perimeter()); // 15
console.log(new Shape().perimeter()); // 0
*/

class Rectangle extends Shape {
    constructor(length = 0, width = 0) {
        super([length, width, length, width]),
            this.length = length,
            this.width = width
    }

    area = () => { return this.sides != NaN ? this.length * this.width : 0 }
}

/*
console.log(new Rectangle(4, 4).perimeter());  // 16
console.log(new Rectangle(4, 4).area());  // 16
console.log(new Rectangle(5, 5).perimeter()); // 20
console.log(new Rectangle(5, 5).area()); // 25
console.log(new Rectangle().perimeter()); // 0
console.log(new Rectangle().area()); // 0
*/
class Triangle extends Shape {
    constructor(sideA = 0, sideB = 0, sideC = 0) {
        super([sideA, sideB, sideC])
        this.side1 = sideA,
        this.side2 = sideB,
        this.side3 = sideC

    }
    //let sum = (this.sideA + this.sideB + this.sideC)/2
    //let root = Math.sqrt(this.sum * (this.sum - this.sideA) * (this.sum - this.sideB) * (sum - this.sideC))
    area = () => {
        const sum = this.perimeter() / 2
        return Math.sqrt(sum * (sum - this.side1) * (sum - this.side2) * (sum - this.side3))
    }
}

/*
console.log(new Triangle(3, 4, 5).perimeter());  // 12
console.log(new Triangle(3, 4, 5).area());  // 6
console.log(new Triangle().perimeter()); // 0
console.log(new Triangle().area()); // 0
*/

// Array of sides arrays
const data = [[3, 4], [5, 5], [3, 4, 5], [10], []];

//plan for each case (traingle, rectangle) create a new shape
//use .length to determine the length of each array element 
//if element length is = to 3, 2, 0 or 1 than the code will output differently 
//case one will be rectangle 
//case 2 triangle
//default will be unsupported  


for (x of data) {
    let num = null;
    switch (x.length) {
        //Rectangle/square 
        case 2:
            let num = new Rectangle(x[0],x[1])
            if(x.length == 2){
        
            if (x[0] == x[1]) {
                console.log(`Square with sides ${x[0]},${x[1]} has a perimeter of ${num.perimeter()} and an area of ${num.area()}`)
            }

            if (x[0] != x[1]) {
                console.log(`Rectangle with sides ${x[0]},${x[1]} has a perimeter of ${num.perimeter()} and an area of ${num.area()}`) 
            }
        }
            break;
        //triangle
        case 3:
            let t = new Triangle(x[0], x[1], x[2])

            if(x.length == 3){
                console.log(`Triangle with sides ${x[0]},${x[1]},${x[2]} has a perimeter of ${t.perimeter()} and an area of ${t.area()}`)
            }
            break;
        default:
            if (x.length == 1) {
                console.log("Shape with 1 side unsupported");
            }
            if (x.length <= 0) {
                console.log("Shape with 0 sides unsupported");
            }
            break;

    }


}




