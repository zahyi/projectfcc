--
-- PostgreSQL database dump
--

-- Dumped from database version 12.17 (Ubuntu 12.17-1.pgdg22.04+1)
-- Dumped by pg_dump version 12.17 (Ubuntu 12.17-1.pgdg22.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(60) NOT NULL,
    hubble_type character varying(30),
    hubble_id integer,
    apparent_magnitude numeric(3,2),
    constellation character varying(30),
    constellation_id integer
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: hubble; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.hubble (
    hubble_id integer NOT NULL,
    name character varying(30) NOT NULL,
    shape text,
    has_bulge boolean,
    has_disk boolean,
    has_arms boolean
);


ALTER TABLE public.hubble OWNER TO freecodecamp;

--
-- Name: hubble_hubble_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.hubble_hubble_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.hubble_hubble_id_seq OWNER TO freecodecamp;

--
-- Name: hubble_hubble_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.hubble_hubble_id_seq OWNED BY public.hubble.hubble_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(60) NOT NULL,
    orbiting_planet character varying(30),
    diameter_in_km numeric(4,2),
    shape text,
    planet_id integer
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    name character varying(60) NOT NULL,
    star_orbiting character varying(60),
    constellation character varying(30),
    has_life boolean,
    star_id integer
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(60) NOT NULL,
    constellation character varying(30),
    galaxy_id integer,
    surface_temperature_in_k integer,
    type text
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: hubble hubble_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.hubble ALTER COLUMN hubble_id SET DEFAULT nextval('public.hubble_hubble_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Centaurus A', 'Lenticular', 3, 6.84, 'Centaurus', 1);
INSERT INTO public.galaxy VALUES (2, 'Caldwell 30', 'Spiral', 1, NULL, 'Pegasus', 2);
INSERT INTO public.galaxy VALUES (3, 'Small Magellanic Clouds', 'Irregular', 5, 2.70, 'Tucana', 3);
INSERT INTO public.galaxy VALUES (4, 'Messier 49', 'Elliptical', 2, NULL, 'Virgo', 4);
INSERT INTO public.galaxy VALUES (5, 'Markarian 231', 'Quasar', 4, NULL, 'Ursa Major', 5);
INSERT INTO public.galaxy VALUES (6, 'Aquarius Dwarf', 'Irregular', 5, NULL, 'Aquarius', 6);
INSERT INTO public.galaxy VALUES (7, 'Milky Way', 'Spiral', 1, -6.50, NULL, NULL);


--
-- Data for Name: hubble; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.hubble VALUES (1, 'Spiral', 'Spherical', true, true, true);
INSERT INTO public.hubble VALUES (2, 'Elliptical', 'Ovular', true, false, false);
INSERT INTO public.hubble VALUES (3, 'Lenticular', 'Disc', true, true, false);
INSERT INTO public.hubble VALUES (4, 'Quasar', 'Emit light', false, false, false);
INSERT INTO public.hubble VALUES (5, 'Irregular', 'Unidentifiable', false, false, false);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 'Moon', 'Earth', 37.93, 'Round', 1);
INSERT INTO public.moon VALUES (2, 'Io', 'Jupiter', 41.91, 'Round', 2);
INSERT INTO public.moon VALUES (3, 'Europa', 'Jupiter', 30.90, 'Round', 2);
INSERT INTO public.moon VALUES (4, 'Ganymede', 'Jupiter', 87.00, 'Round', 2);
INSERT INTO public.moon VALUES (5, 'Callisto', 'Jupiter', 73.00, 'Round', 2);
INSERT INTO public.moon VALUES (6, 'Mimas', 'Saturn', 0.49, 'Round', 3);
INSERT INTO public.moon VALUES (7, 'Enceladus', 'Saturn', 0.79, 'Round', 3);
INSERT INTO public.moon VALUES (8, 'Tethys', 'Saturn', 3.57, 'Round', 3);
INSERT INTO public.moon VALUES (9, 'Dione', 'Saturn', 3.97, 'Round', 3);
INSERT INTO public.moon VALUES (10, 'Rhea', 'Saturn', 7.34, 'Round', 3);
INSERT INTO public.moon VALUES (11, 'Titan', 'Saturn', 83.00, 'Round', 3);
INSERT INTO public.moon VALUES (12, 'Iapetus', 'Saturn', 6.70, 'Round', 3);
INSERT INTO public.moon VALUES (13, 'Miranda', 'Uranus', 0.70, 'Round', 4);
INSERT INTO public.moon VALUES (14, 'Ariel', 'Uranus', 4.21, 'Round', 4);
INSERT INTO public.moon VALUES (15, 'Umbriel', 'Uranus', 4.29, 'Round', 4);
INSERT INTO public.moon VALUES (16, 'Titania', 'Uranus', 7.82, 'Round', 4);
INSERT INTO public.moon VALUES (17, 'Oberon', 'Uranus', 7.29, 'Round', 4);
INSERT INTO public.moon VALUES (18, 'Proteus', 'Neptune', 0.55, 'Ellipsiod', 5);
INSERT INTO public.moon VALUES (19, 'Triton', 'Neptune', 23.01, 'Round', 5);
INSERT INTO public.moon VALUES (20, 'Charon', 'Pluto', 4.58, 'Round', 6);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 'Earth', 'Sun', NULL, true, 1);
INSERT INTO public.planet VALUES (2, 'Jupiter', 'Sun', NULL, false, 1);
INSERT INTO public.planet VALUES (3, 'Saturn', 'Sun', NULL, false, 1);
INSERT INTO public.planet VALUES (4, 'Uranus', 'Sun', NULL, false, 1);
INSERT INTO public.planet VALUES (5, 'Neptune', 'Sun', NULL, false, 1);
INSERT INTO public.planet VALUES (6, 'Pluto', 'Sun', NULL, false, 1);
INSERT INTO public.planet VALUES (7, 'Proxima Centauri D', 'Proxima Centauri', 'Centaurus', false, 2);
INSERT INTO public.planet VALUES (8, '51 Pegasi b', '51 Pegasi', 'Pegasus', false, 3);
INSERT INTO public.planet VALUES (9, 'Pipitea', 'Poerava', 'Tucana', false, 4);
INSERT INTO public.planet VALUES (10, 'Poltergeist', 'Lich', 'Virgo', false, 5);
INSERT INTO public.planet VALUES (11, 'Taphao Thong', 'Chalawan', 'Ursa Major', false, 6);
INSERT INTO public.planet VALUES (12, 'Trappist 1', 'Trappist-1', 'Aquarius', false, 7);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (2, 'Proxima Centauri', 'Centaurus', 1, 3042, 'red dwarf');
INSERT INTO public.star VALUES (3, '51 Pegasi', 'Pegasus', 2, 5768, 'yellow dwarf');
INSERT INTO public.star VALUES (4, 'Poerava', 'Tucana', 3, 6440, 'F-type');
INSERT INTO public.star VALUES (5, 'Lich', 'Virgo', 4, 2300, 'pulsar');
INSERT INTO public.star VALUES (6, 'Chalawan', 'Ursa Major', 5, 5882, 'yellow dwarf');
INSERT INTO public.star VALUES (7, 'Trappist-1', 'Aquarius', 6, 2566, 'red dwarf');
INSERT INTO public.star VALUES (1, 'Sun', NULL, 7, 5800, 'yellow dwarf');


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 1, false);


--
-- Name: hubble_hubble_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.hubble_hubble_id_seq', 1, false);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 1, false);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 1, false);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 1, false);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: hubble hubble_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.hubble
    ADD CONSTRAINT hubble_name_key UNIQUE (name);


--
-- Name: hubble hubble_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.hubble
    ADD CONSTRAINT hubble_pkey PRIMARY KEY (hubble_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: galaxy galaxy_hubble_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_hubble_id_fkey FOREIGN KEY (hubble_id) REFERENCES public.hubble(hubble_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

