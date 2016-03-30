var test = require('tape')


var nestedExampleObject = {
  head: 'cats',
  tail: {
    head: 'dogs',
    tail: {
      head: 'rabbit'
    }
  }
}


// finds the deepest level of nestedThing
function findBottomAnimal( nestedObject, headCollection ) {
  headCollection = headCollection || []

  var animalHeads = nestedObject.head
  headCollection.push(animalHeads)


  // look inside the nestedObject
  // if there's no tail inside the nestedObject, we're at the 'bottom'
  if(nestedObject.tail === undefined){
    return headCollection
  }

  // add the current head to the collection


  // return the head at this level
  var result = findBottomAnimal(nestedObject.tail, headCollection)
  return result

  // if we found a tail, we want to 'step inside' that tail,
  // and run 'findBottomAnimal' again on this
  // save the result of this 'deeper' findBottomAnimal
  // return this result
}



