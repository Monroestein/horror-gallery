<template>
    <main>

        <!-- Sidebar -->
        <div class="sideMain">
            <Sidebar 
                v-for="character in characters" 
                :id="character.id"
                :image="character.image" 
                :key="character.id"
                @showDesc="popUpDescription"
            ></Sidebar>
        </div>
       
        <!-- Content when clicked -->
        <div class="contMain">
            <div v-if="selectedCharacter">
                <Content
                     :id="selectedCharacter.id"
                     :name="selectedCharacter.name"
                     :movie="selectedCharacter.movie"
                     :description="selectedCharacter.desc"
                     :image="selectedCharacter.image"
                     :key="selectedCharacter.id"    
                ></Content>
            </div>
        </div>

    </main>
</template>

<script>

import Sidebar from './Sidebar.vue'
import Content from './Content.vue'

    export default {
        name: 'gallery-comp',
        data: function(){
            return {
                characters:[
                    {
                        id: 1,
                        name: 'Leatherface',
                        movie: 'The Texas Chainsaw Massacre',
                        desc: `He is usually portrayed as mentally handicapped and wears a mask made out of human skin, which leads to his eventual name - Leatherface.
                        The character is loosely based on the real-life serial killer Ed Gein, who is remembered as one of the most brutal serial killers in American history, whom also happened to skin his victims alive and wear clothes made out of their skin. Leatherface is usually depicted with his iconic chainsaw, but he is also known for using a large sledgehammer to attack his victims.`,
                        image: 'https://static1.cbrimages.com/wordpress/wp-content/uploads/2020/05/Leatherface-Texas-Chainsaw-Massacre-Featured.jpg'
                    },
                    {
                        id: 2,
                        name: "The Monster",
                        movie: 'Frankenstein',
                        desc: "Victor Frankenstein builds the creature over a two-year period in the attic of his boarding house in Ingolstadt after discovering a scientific principle which allows him to create life from non-living matter. Frankenstein is disgusted by his creation, however, and flees from it in horror. Frightened, and unaware of his own identity, the monster wanders through the wilderness. He finds solace beside a remote cottage inhabited by an older, blind man and his two childre",
                        image: 'https://static01.nyt.com/images/2018/10/28/arts/28frankenstein-movies1/merlin_15260757_3b7e90b8-2358-43e4-970e-8eb4424dba86-superJumbo.jpg'
                    },
                    {
                        id: 3,
                        name: 'Jason Vorhees',
                        movie: 'Friday the 13th',
                        desc: "Either as a figment of imagination or in the flesh, Jason appears in every novel, comic, and film. Jason stalks and kills the Camp Crystal Lake, feeling a burning need to avenge the death of his beloved mother, Pamela, and the abuse they received, largely due to Jason's deformity. He has only one copycat killer, Roy Burns.",
                        image: 'https://cdn.hobbyconsolas.com/sites/navi.axelspringer.es/public/media/image/2014/05/327826-novedades-serie-viernes-13-nuevo-jason-voorhees.jpg?tf=3840x'
                    },
                    {
                        id: 4,
                        name: 'Pazuzu',
                        movie: 'The Exorcist',
                        desc: "Being a Judeo-Christian demon, Pazuzu was created as an angel to worship and serve God. After rebelling against God with Lucifer, God banished them and all their cohorts from Heaven, and they became demons. As a demon, Pazuzu sought to violate and destroy God's favored creation, humans. He took the form of a pale skinned human-like ghoul, with brown irises, sagging lower eyelids, and yellow teeth. Sects of humans. who worshipped him as a deity, depicted him in statues with stubby horns, sharp teeth, two pairs of eagle-like wings, and a long, serpentine penis.",
                        image: 'https://static1.srcdn.com/wordpress/wp-content/uploads/2023/05/the-exorcist-pazuzu.jpg'
                    },
                    {
                        id: 5,
                        name: 'Count Dracula',
                        movie: 'Dracula',
                        desc: "Count Dracula is a vampire that through a deal with the devil has existed for centuries, also the character is of Transylvanian nobleman birthright and is a practitioner of sorcery. The character has claimed to be of Szelsky origin and related to Atilla the Hun. Dracula maintains residence in a ruined castle in the Carpathian mountains near The Borgo Pass, situated in far Eastern Europe which has become quite a popular setting for the character.",
                        image: 'https://lehighvalleymarketplace.com/wp-content/uploads/2015/12/dracula-2220x1200.jpg'
                    },
                    {
                        id: 6,
                        name: 'Freddy Krueger',
                        movie: 'A Nightmare on Elm Street',
                        desc: "Amanda Krueger was a nun working in a hospital, and was raped by over 100 psychopaths. She became pregnant with a son, who was named Freddy. Later in his life, he became a murderer in Springwood notorious for killing children. The media labeled him the Springwood Slasher. He was apprehended, but later released because of a technicality. According to the original film, it was because someone didn't sign the search warrant in the appropriate place. The parents of the children tracked him down and found him in the boiler room where he took his victims. The parents poured gas into the room and set him on fire, which caused his melted-like facial features.",
                        image: 'https://maquillajestudio.cl/wp-content/uploads/2016/07/Freddy-Krueger1.jpg'
                    },
                    {
                        id: 7,
                        name: 'Michael Myers',
                        movie: 'Halloween',
                        desc: "As a child, Michael was admitted into a psychiatric hospital for the murder of his older sister, Judith Myers. After 15 years of captivity, Myers broke out of the asylum and started his killing spree, with the intention to murder his remaining family relatives and anyone who would get in his way.",
                        image: 'https://media.gq.com.mx/photos/5be9c35ef0f5ac76ac143c0f/4:3/w_2668,h_2001,c_limit/john_carpenter_inspiracion_de_michael_myers_en_halloween_asesino_435.jpg'
                    },
                    {
                        id: 8,
                        name: 'Pinhead',
                        movie: 'Hellraiser',
                        desc: "As a human, he was Elliot Spencer, a captain in World War I. But then, ever since he solved the Lament Configuration, he was sucked into Hell and transformed into a Cenobite. Several decades later, he rose out of Hell for the first time.",
                        image: 'https://preview.redd.it/what-is-your-opinion-on-pinhead-i-maybe-see-him-once-a-week-v0-x5fg27wpdvua1.jpg?auto=webp&s=430df1f1581c460927485e0c05f05dbbd392f96a'
                    },
                    {
                        id: 9,
                        name: 'Chucky',
                        movie: "Child's Play",
                        desc: "In his human form, Chucky was a rather attractive looking Caucasian male with shoulder-length brown hair and piercing eyes and wears a trench coat or blazer and white sneakers. However, this changes once he enters the doll. He has long, red hair and freckles, along with blue eyes. He wears blue overalls, a striped, multicolored shirt, and sneakers. Throughout the first three films of the series he looks like an everyday child's doll, but with the fourth film came his famous scars and stitches, as well as a bloody eye.",
                        image: 'https://www.lavanguardia.com/andro4all/hero/2024/04/chucky.jpg?width=1200'
                    },
                    {
                        id: 10,
                        name: 'Ghostface',
                        movie: 'Scream',
                        desc: "Ghostface is named after the rubber mask under which he hides his face, a mask inspired by the Edvard Munch painting The Scream. He is also known as the Woodsboro Killer, after the town where he commits his murders. Ghostface often calls his victims on the phone, taunting or threatening them before stabbing them to death with an 8 inch bowie knife or killing them any other way. He is usually known for asking their victims horror film trivia while stalking them. All ghostface people always die.",
                        image: 'https://people.com/thmb/zb9pb18cWVP2SJKjQ6LItJp24Sg=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():focal(1099x78:1101x80)/Scream_03-1c6647feac364a8e89598b9fbb7897c8.jpg'
                    },
                    {
                        id: 11,
                        name: 'Valak',
                        movie: 'The Conjuring',
                        desc: "Valak is an evil, cold and tough demon, who has an intention to terrify the Hodgen Family house by causing strange things to the Warrens. Bill Wilkins, who seemed to be the one responsible, was none other than a disguise of Valak himself. The real Bill's spirit was just a pawn for it. Valak is a powerful demonic spirit, who wants to drive his entire victims that he is possessed into suicide and murder. Valak is an evil, murderous, and very tough being.",
                        image: 'https://static0.srcdn.com/wordpress/wp-content/uploads/2021/06/Valak-The-Conjuring-2-vision.jpg'
                    },
                    {
                        id: 12,
                        name: 'It',
                        movie: 'It',
                        desc: "It apparently originated in a void containing and surrounding the, a place referred to in the novel as the 'Macroverse' (a concept similar to the later established Todash Darkness of The Dark Tower series). It's real name is unknown, it possibly has no name. If it does, then it is probably of a supernatural language the human mind won't understand. However IT claims to be named Robert 'Bob' Gray or Pennywise (Though IT could be just toying with the losers club) and is christened 'It' by the group of children who later confront It. Likewise, It's true form is never truly comprehended.",
                        image: 'https://deadline.com/wp-content/uploads/2022/03/BM_Pennywise_battery_acid_makeup_1-e1646914981720.jpeg'

                    },
                    {
                        id: 13,
                        name: 'Xenomorph',
                        movie: 'Alien',
                        desc: "The Xenomorphs are vicious predatory creatures with no higher goals than the propagation of their species and the destruction of any life that could pose a threat to them. Like wasps, ants or bees, Xenomorphs are eusocial, with a fertile Queen breeding a host of subordinate castes. The creatures are known for their potent acid blood, tails and their inner jaws, although their biological life cycle, in which their offspring are implanted inside living hosts before erupting violently from their chests, is in many ways their signature aspect.",
                        image:'https://www.indiewire.com/wp-content/uploads/2017/04/alien1.jpg'
                    },
                    {
                        id: 14,
                        name: 'Three Finger',
                        movie: 'Wrong Turn',
                        desc: "Three finger is considered to be the most psychotic out of his brothers. He constantly toys with his prey using an ominous cackle of laughter and clicking noises. Like all the cannibals he consumes human flesh on a regular basis and shows no moral side for any that are not his kin(however he did give Cruz an unsettling playful affection while he was feeding her intestines to her). Three finger is shown to be a very creative and skilled trapper.",
                        image: 'https://static1.srcdn.com/wordpress/wp-content/uploads/2020/04/Three-Finger-Wrong-Turn-2003.jpg'
                    }
                ],
                selectedCharacter: null
            }
        },
        components: {
            Sidebar,
            Content
        },

        methods: {
            popUpDescription(id){
                const character = this.characters.find(character => character.id == id)
                console.log(character)
                this.selectedCharacter = character
            }
        }
    }
</script>

<style scoped>

main{
    border: 1px solid #3b3b3b;
    width: 70%;
    max-height: 650px;
    margin: 40px auto;
    display: flex;
    background: #1d1d1d;
}

.sideMain{
    flex-grow: 1;
    display: flex;
    min-width: 270px;
    max-width: 270px;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    overflow: auto;
    padding: 1rem;
    scrollbar-width: thin;
    scrollbar-color: #444 #222;
}

.contMain{
    flex-grow: 2;
}

</style>